---
layout: default
title: Sensitive integrations
permalink: /integrations/
nav: integrations
---

# Sensitive integrations

This page is **what the community needs to grow** — capabilities, seams, and rules. It is not a key vault, a vendor signup walkthrough, or a list of credentials the private desk may hold.

**Never paste secrets into issues, pull requests, screenshots, or chat.**

If you found a key in a commit, gist, or log, see [SECURITY.md](https://github.com/fh2fcr42z2-glitch/helix-community/blob/main/SECURITY.md). Do not echo the secret back.

## Why API keys and paid feeds are gated

Some research questions are cheap. Some are licensed, personal, or easy to steal.

| Capability | Why it is gated | If it is missing |
| --- | --- | --- |
| **Wallet identity** | Clustering and labels are vendor IP; they can also identify people | Field is DARK. Do not guess “smart money” from a DEX screenshot |
| **Smart money / labeled wallets** | Paid attribution (GMGN, Helius, Birdeye, Nansen, Arkham). Easy to overfit and leak | DARK. Scout may still use public FLOW + Trends + chatter |
| **CEX entity flow** | Exchange-sensitive; CryptoQuant / Glassnode unpaid stay DARK; easy to misread | DARK. Do not invent inflow/outflow from price |
| **Bridge netflow** | DefiLlama **Pro** (not the free TVL/volume surface) | DARK. Do not back-solve bridges from TVL |
| **Full SIP tape** | US equity consolidated tape is a licensed product | Equities sidecar stays DARK. Crypto public CEX/DEX is the free path |
| **Options flow** | Expensive, redistribution-restricted, easy to market as a crystal ball | DARK. Not a crypto-first requirement |
| **X auto-post** | Distribution is not research; posting tokens are secrets | **Off.** A NOTE is a document, not a bot |
| **WordPress live publish** | Application passwords and live CMS writes are out of scope | **DARK.** Draft-only future — never auto-publish |

Gating is not mystique. It is **license, cost, and privacy**. The public bench must run — and test — without those keys.

A key that exists only on one person’s laptop does not exist for CI, for reviewers, or for this repo. **Only read-only research keys** are even in scope as future placeholders. Swap, withdraw, trading-session, and publish tokens are not research keys.

## Standing DARK list

Until an adapter + mock exists *and* (for gated rows) a read-only key exists in a private environment, treat these as **DARK**. Named vendors are not a claim that Helix is wired to them.

| DARK item | Typical vendor / why | Public stance |
| --- | --- | --- |
| **Bridge netflow** | DefiLlama **Pro** | Free Llama is chain stables + TVL + DEX vol only ([FLOW.md](FLOW.md)) |
| **Labeled wallets** | GMGN, Helius, Birdeye (also Nansen, Arkham) | Wallet rung of FLOW stays DARK |
| **CEX entity flow** | CryptoQuant, Glassnode **unpaid** | No implied exchange whales |
| **X auto-post** | Twitter/X posting API | Off. No community bot |
| **WordPress publish** | Live CMS / application passwords | Draft-only future; not in this repo |

Do not fill DARK with fiction. Unknown is a first-class state.

## Placeholder capability matrix

This matrix is a **menu of unlocks**, not an inventory of shipped adapters. If you have not seen a working adapter + mock test in a public PR, treat the row as **aspirational**.

**What it unlocks** = the research question you can ask *after* a private environment has a credential. It does not mean Helix currently answers that question.

### Free / public (no key, or keyless public endpoints)

Use these to build the default desk. Rate limits still apply; cache politely; read each vendor’s terms.

| Source | What it unlocks |
| --- | --- |
| **Coinbase** | Public CEX spot tape and product metadata for major pairs — a real bar source |
| **Kraken** | A second public CEX tape so you can cross-check prints and holes |
| **CoinGecko** | Aggregated coin identity, caps, and public prices — universe building, not a matching engine |
| **DefiLlama (free)** | Chain-rung FLOW: stables, TVL, DEX volume aggregates — not bridge netflow, not wallets |
| **DEX Screener** | DEX-rung pair stats for FLOW (liquidity, advertised volume) — not labeled flow |
| **GeckoTerminal** | Public DEX pool / OHLCV-style series for on-chain markets |
| **Google Trends** | Search-interest series — the search leg of social arbitrage |

If a pair or topic is absent from these sources, the honest output is **not listed / DARK**, not a generated candle.

### Optional / paid (keyed, licensed, or both)

Bring-your-own **read-only research** key in a **private** environment. Do not commit the key. Do not ask maintainers to paste theirs. If the key can swap, withdraw, or post, it does not belong here.

| Source | What it unlocks |
| --- | --- |
| **DefiLlama Pro** | Bridge netflow and other Pro-only FLOW — still DARK on the free bench |
| **Helius** | Solana RPC / richer on-chain reads — wallet-level *possibility* when a **read-only** key exists |
| **Birdeye** | Token-level market analytics and possible wallet reads (often Solana/EVM) — keyed, easy to over-claim |
| **GMGN** | Labeled-wallet / smart-money-style screens — gated; wallet FLOW stays DARK without it |
| **Nansen** | Wallet labels and smart-money-style attribution — gated, easy to misuse |
| **Arkham** | Entity / wallet intelligence — gated; treat as PII-adjacent |
| **CryptoQuant** | CEX entity flow and related metrics — **unpaid = DARK** |
| **Glassnode** | Broader on-chain indicator sets — **unpaid = DARK** |
| **Tiingo** | Paid market / news / fundamentals-style coverage; relevant to a **future equities sidecar** |
| **IBKR** | Named only as a future equities **sidecar interface**. **Trading / swap connectors stay off** |

Other vendors will look like these rows: a **port**, an **adapter**, a **mock**, a **DARK path**. Open an issue before adding a new name so we do not collect logos for sport.

### Intentionally blank (DARK until proven)

Do not fill these with fiction. The standing list above plus:

- Any wallet cluster you cannot cite from a keyed adapter or a public, license-clean source
- SIP-quality US equity prints
- Options unusual-flow narratives
- “Whale bought” without a wallet source
- Synthetic OHLCV used as if it printed
- Bridge netflow inferred from TVL
- An X post or WordPress URL presented as “the desk published”

Unknown is a first-class state. **DARK** is more useful than a pretty chart.

### Swap and trading connectors stay off

There is no community port for swaps, CEX orders, routers, or withdraw. Sentinel rejects PRs that add them “for completeness.” IBKR and similar names in the matrix are **not** an invitation to wire a session. Paper book only.

## How contributors can help

You do not need a Nansen seat to be useful.

1. **Adapters behind interfaces**  
   Implement one port (`Tape`, `SearchInterest`, `ChainFlow`, `DexVolume`, `TokenBoard`, …) for one vendor. Accept config from the environment. If the key is absent, return DARK — do not crash the desk, do not fill zeros that look like prices. **Read-only research keys only.**

2. **Tests with mocks**  
   Fixture the JSON. Assert parse + mapping + DARK behavior. CI should go green on a laptop that has never seen a vendor dashboard.

3. **Docs**  
   Correct this matrix when a public API changes. Mark a row DARK if we over-claimed. Add a rate-limit or attribution note. Do not add “setup: here is our key.”

4. **Paper strategy ideas**  
   Follow the skeleton in [CONCEPT.md](CONCEPT.md). Name the three legs and the DARK list. No live-trading language.

5. **Rate-limit and failure hygiene**  
   Backoff, cache, and explicit empty states. A polite free-tier client is a contribution.

6. **Interface RFCs**  
   Propose a port before a fourth ad-hoc client. Small write-up, then a thin adapter.

See [CONTRIBUTING.md](CONTRIBUTING.md) for issue and PR shape.

## Security rules for contributors

- **Local `.env` only.** Load keys from the environment. A committed `.env` is a breach, even if you think the repo is private.
- **Never commit secrets.** That includes tokens in `README`, notebooks, screenshots, HAR files, and “temporary” debug logs.
- **Never paste secrets into GitHub.** Not in issues, not in review comments, not in Actions logs you then screenshot.
- **Redact.** If a test needs a shape, use a clearly fake placeholder such as `example-not-a-real-key`. Do not use a live key with a character missing.
- **Report leaks.** If you see a real key, follow [SECURITY.md](https://github.com/fh2fcr42z2-glitch/helix-community/blob/main/SECURITY.md). Do not open a public issue that contains the key.
- **Sentinel stays on.** Community PRs that add a live `create_order`, swap, or router path will be rejected.
- **Read-only only.** Future keys are research reads. No spend, no trade, no auto-post.
- **Vendor terms.** Scraping around a paywall or sharing a login is not a contribution.

```
# local only — names, not a real inventory
#   cp .env.example .env
#   # put read-only research keys in .env; .env is gitignored

COINGECKO_DEMO_KEY=    # optional even for "free" tiers
HELIUS_API_KEY=        # optional / paid / read-only
DEFILLAMA_PRO_KEY=     # optional; bridge netflow stays DARK if blank
GMGN_API_KEY=          # optional; labeled wallets stay DARK if blank
# do not add swap, trading, X, or WordPress secrets — not even blank "for later"
```

`.env.example` may list **names** of read-only research variables. It must not list values. It must not list trading or publish credentials.

## What maintainers will never ask you for

- Your exchange password or 2FA
- A production wallet seed
- A dump of the private helix-cx repo
- Permission to “just run live once to see”
- An X or WordPress token “so we can auto-post the NOTE”
- A swap or trading API key, even “read-write for later”

If a person claiming to be a maintainer asks for those, it is not part of this community process.
