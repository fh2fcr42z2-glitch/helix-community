# PnL honesty

Public contract for the **PnL panel**. Private wiring lives on helix-cx **PR #1**. This repo documents the rules — not the client.

**Never invent PnL.** Viral screenshots and bot threads stay **DARK** — not Helix evidence. No fabricated totals. Unknown → **DARK** with a reason.

Connect / DEX visibility: [WALLET-LOGIN.md](./WALLET-LOGIN.md). MM vault rails: [MARKET-MAKER.md](./MARKET-MAKER.md).

## Cross-source PnL (three books, labeled)

The panel may **read** three sources. They are **not** one blended book. Each line keeps its own as-of, provenance, and DARK list.

| Source | What it may show | How it is labeled | If missing |
|---|---|---|---|
| **Coinbase** | Account fills / marks the user authorized Helix to **read** | `source=coinbase` | Key/OAuth blank, 401, timeout → **DARK** + reason. Public Coinbase *tape* ≠ this row |
| **Connected wallets** | The user’s own SIWS/SIWE addresses via real RPC / free APIs | `source=wallet` + chain + address | Not connected, RPC fail, unsupported chain → **DARK** + reason. [WALLET-LOGIN.md](./WALLET-LOGIN.md) |
| **MM `fee_income`** *(optional)* | Journaled fee-vault rotate PnL with `source_id` | `source=mm_fee_income` — **separate** from Coinbase and wallets | Missing journal / fee source DARK → **DARK**. Never stub fees. **Principal is not PnL** |

Do not collapse Coinbase + wallets + `fee_income` into an unlabeled “Helix total.” Optional MM `fee_income` stays a **separate labeled line** even when all three are LIVE.

`principal` is locked and **out of the PnL card** as tradable stake. Do not report principal marks as MM performance.

HYPE sleeve PnL stays **DARK until adapter** — a connected wallet or a Coinbase row does not light it.

## Never invent

| Allowed | Forbidden |
|---|---|
| Real fills / marks with **as-of** + **provenance** (`source_id`) | A number with no source |
| Viral posts as *process* inspiration | Viral PnL as a Helix total, backtest, or missing-source fill |
| Per-source lines that are LIVE or DARK | Silent `0` when a source failed |
| Tests with **labeled mocks** | Demo totals in the desk UI |

A spinner is not `0`. Last-known is not live. Coinbase tape is not Coinbase **account** PnL. Another person’s wallet cluster is not this panel ([FLOW.md](./FLOW.md) wallet rung stays DARK).

## Realized / unrealized / fees

Every source that is LIVE splits the same three fields. Missing field → **DARK**, not a guessed remainder.

| Field | Meaning | Honest source | If missing |
|---|---|---|---|
| **Realized** | Closed fills, net of the fee field below | Venue/account API or wallet decode with as-of | **DARK** — do not back-solve from a screenshot |
| **Unrealized** | Open inventory marked from a **real** tape | Same mark rules as the desk (real bar or DARK) | **DARK** — do not use a synthetic mid |
| **Fees** | Paid fees / gas with `source_id` | Coinbase fee line, chain tx fees, MM fee journal | **DARK** / SKIP — **never stub fees** |

Each field carries **as-of** (when the observation was taken) and **provenance** (`source_id`, venue or chain, adapter). Forbid `pnl` / `fees` / `mids` without `source_id` — same rule as the MM journal.

Do not net realized against unrealized to hide a DARK leg. Do not drop fees so the number looks bigger.

## Incomplete aggregate badge

A headline total is **complete** only if every source the panel claims to include is LIVE.

If **any** included source is DARK (Coinbase, a connected-wallet chain, or optional `fee_income` when that line is in the card):

1. Show an **incomplete aggregate** badge (not a quiet smaller total).
2. Keep per-source rows visible: LIVE numbers and DARK reasons.
3. Do **not** fabricate a total that pretends the DARK source was `0` or “not applicable.”
4. Do **not** omit the DARK source from the legend so the sum looks finished.

Unmeasured ≠ complete. Partial Coinbase + live wallets is still **incomplete**. Optional `fee_income` off the card is not DARK; optional `fee_income` *on* the card and missing **is** DARK → badge.

## Env names only (Coinbase keys / OAuth)

Private env, gitignored. **Names**, never example secrets, client ids, or redirect URLs-with-tokens.

| Name | Role |
|---|---|
| `COINBASE_API_KEY` | Read-only Coinbase account / Advanced Trade key for fills and marks |
| `COINBASE_API_SECRET` | Matching secret. Local only |
| `COINBASE_OAUTH_CLIENT_ID` | OAuth app id if the desk uses Coinbase OAuth instead of (or in addition to) API keys |
| `COINBASE_OAUTH_CLIENT_SECRET` | OAuth client secret. Local only |

Blank, missing scope, or 401 → Coinbase PnL is **DARK**. Public Coinbase market data (already FREE on the Scout catalog) does **not** fill this hole.

Wallet RPC names stay in [WALLET-LOGIN.md](./WALLET-LOGIN.md) (`SOLANA_RPC_URL`, `ETH_RPC_URL`). Do not commit `.env`. Do not paste these values into PRs. Trading, withdraw, and spend scopes stay **off** — this panel is a **read**. Swap connectors stay off.

## What this is not

- A blended “all-crypto PnL” with no provenance
- Viral bot / sniper dollar claims ([MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md), [CREW-HANDOFF.md](./CREW-HANDOFF.md))
- MM `principal` performance, or `fee_income` mixed into Coinbase without a label
- Fake completeness when any source is DARK
- A Coinbase **trading** connector (Sentinel still forbids unsupervised live orders in community code)

## Private implementation

PnL panel wiring: **helix-cx PR #1**. Public `helix-community` does not copy that client.

Desk truth: [STATUS.md](./STATUS.md). Connect: [WALLET-LOGIN.md](./WALLET-LOGIN.md). MM: [MARKET-MAKER.md](./MARKET-MAKER.md).
