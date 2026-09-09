# Wallet login + DEX visibility

Public contract for **connect** and the **portfolio / DEX panel**. Private wiring lives on helix-cx **PR #1** (connect + DEX view). This repo documents the rules — not the client.

**Helix never holds keys.** No custodial vaults in v1. No silent auto-sign. **No fake balances.** Unknown → **DARK** with a reason.

Connect does not loosen Market Maker rails: `fee_income` only, **principal locked**, kill / SKIP. See [MARKET-MAKER.md](./MARKET-MAKER.md) and [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## Connect model (SIWS + SIWE)

The user signs. Helix verifies. Helix does **not** take the key.

| Chain family | Login | What Helix keeps | What Helix never keeps |
|---|---|---|---|
| **Solana** | **SIWS** (Sign-In with Solana) — user signs a login message | Verified **address** + a view session | Seed, private key, spend-capable session |
| **EVM** | **SIWE** (Sign-In with Ethereum) — user signs a login message | Verified **address** + a view session | Seed, private key, WalletConnect pairing secret |

That signature is **proof of address control at login**, not a spending grant.

WalletConnect (or a chain-native wallet popup) is a **transport**. The env **name** is `WALLETCONNECT_PROJECT_ID`. Never paste a project id, keyed RPC URL, or pairing secret into issues, PRs, or this repo.

Connect does **not**:

- Unlock `principal`
- Invent a `fee_income` balance
- Light the **HYPE** sleeve
- Turn labeled-wallet FLOW on (Nansen / Arkham / GMGN stay **DARK** without a verified free source — [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md))
- Authorize swaps, withdraws, or silent MM quotes

## “Act on behalf” = propose → popup

v1 is **non-custodial**. Helix may **propose** an action (an MM rotate on `fee_income`, a cancel/replace, a kill pull). The **wallet popup** is the signer. The user confirms or rejects.

| Allowed | Forbidden |
|---|---|
| Propose a payload; wait for the wallet UI | Silent auto-sign / pre-approved session spend in v1 |
| One popup per action the user can read | Batch-sign “whatever the desk wants this hour” |
| User rejects → journal SKIP / veto; no stub fill | Retry until the wallet gives in |
| Session = logged-in address for **view** | Session = spend authority or a Helix-held vault |

**No custodial vaults in v1.** Dual-vault MM (`principal` read-only · `fee_income` tradable stake) is **desk bookkeeping**, not Helix holding keys. Keys stay in the user’s wallet. Helix does not run a hot wallet, a pooled vault, or an “act without asking” relayer in this version.

## Chains (same sleeves as MM)

| Sleeve | Connect / panel | Honest note |
|---|---|---|
| **SOL** | **Primary** | SIWS + Solana RPC / free DEX APIs. Still fail-closed if *this pair’s venue* is DARK |
| **ETH** | **Try-now** | SIWE + ETH RPC. Gas as-of required for MM; missing gas → SKIP, never eat principal |
| **HYPE** | **DARK until adapter** | Connecting a wallet does **not** make Hyperliquid quotable. Sleeve stays DARK until a mocked adapter exists |

Do not show a HYPE book, HYPE inventory, or HYPE `fee_income` because SIWE/SIWS succeeded.

## Portfolio / DEX panel

The panel is a **read**. It is not a tape, not a whale label, and not a PnL card.

| Field | Honest source | If missing |
|---|---|---|
| Connected address | SIWS / SIWE verify | Not logged in — no portfolio |
| Native / token balances | **Real** RPC (`SOLANA_RPC_URL`, `ETH_RPC_URL`) or a named free API | **DARK** + reason (timeout, 401, 429, unsupported chain) |
| DEX pair / LP context | Free desk APIs already in the Scout catalog (DEX Screener, GeckoTerminal, DefiLlama-class) | **DARK** + reason — do not average into a fake DEX tape |
| MM vault split | Journal `fee_income` / `principal` with `source_id` | Missing source → SKIP / DARK — **never stub fees** |

**No fake balances.** A spinner is not `0`. A demo fixture belongs in tests and must be labeled mock. Do not paint last-known numbers after RPC failure. Do not backfill ETH from SOL, or HYPE from a screenshot.

Showing **the user’s own** on-chain balances via public RPC is not WalletIdentity / smart-money labels. Clustering other people’s wallets stays **DARK**.

## Env names only (no values)

Private env, gitignored. **Names**, never example ids or URLs-with-keys.

| Name | Role |
|---|---|
| `WALLETCONNECT_PROJECT_ID` | WalletConnect Cloud project id for the connect transport |
| `SOLANA_RPC_URL` | Solana JSON-RPC for reads (balances, accounts). Keyed URLs stay local |
| `ETH_RPC_URL` | Ethereum JSON-RPC for reads. Keyed URLs stay local |

Blank → that read is **DARK**. Do not commit `.env`. Do not paste these values into PRs. Do not add spend keys, session secrets, or WalletConnect pairing keys to `.env.example`.

Optional research RPC names already catalogued (`HELIUS_API_KEY`, `ALCHEMY_API_KEY`) are **read-only** — still DARK when blank, still not labels, still not custody.

## Fits MM rails

Connect is identity + visibility. It does not change [MARKET-MAKER.md](./MARKET-MAKER.md):

1. **`fee_income` only** — tradable stake. Login does not debit `principal`.
2. **Principal locked** — read-only vault. A connected wallet is not permission to spend it.
3. **Kill ON** → code stops new entries (popup or not).
4. **SKIP** — `fee_income` 0 or fee source DARK; ETH gas over budget / stale; user rejects the popup.
5. **Venue DARK → block** — including **HYPE until adapter**. A connected address is not a venue adapter.
6. Journal still needs `source_id` on balances, fees, mids. Forbid invented PnL.

Propose → popup is the only v1 path that can move `fee_income`. Sentinel still forbids unsupervised live connectors in community code.

## What this is not

- A Helix-held key, MPC vault, or “we’ll sign in the cloud”
- Silent auto-sign / session spend in v1
- Fake portfolio numbers for a screenshot
- Labeled wallets, bridges, or entity flow ([FLOW.md](./FLOW.md) wallet rung stays DARK)
- A swap / router / withdraw port
- Lighting HYPE because WalletConnect lists “many chains”

## Private implementation

Connect + DEX view wiring: **helix-cx PR #1**. Public `helix-community` does not copy that client. If private GitHub `main` is still a hull, say so once and use [STATUS.md](./STATUS.md).

Desk truth: [STATUS.md](./STATUS.md). MM process: [MARKET-MAKER.md](./MARKET-MAKER.md). Sleeves: [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).
