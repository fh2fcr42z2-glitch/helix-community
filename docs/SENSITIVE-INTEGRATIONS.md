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
| **Smart money** | Paid attribution. Easy to overfit and easy to leak via copied dashboards | DARK. Scout may still use public tape + Trends + chatter |
| **CEX flow** | Exchange-sensitive; often contract-limited; easy to misread | DARK. Do not invent inflow/outflow from price |
| **Full SIP tape** | US equity consolidated tape is a licensed product | Equities sidecar stays DARK. Crypto public CEX/DEX is the free path |
| **Options flow** | Expensive, redistribution-restricted, easy to market as a crystal ball | DARK. Not a crypto-first requirement |

Gating is not mystique. It is **license, cost, and privacy**. The public bench must run — and test — without those keys.

A key that exists only on one person’s laptop does not exist for CI, for reviewers, or for this repo.

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
| **DefiLlama** | Protocol TVL and related DeFi aggregates — context, not a wallet |
| **DEX Screener** | Public DEX pair screens, liquidity, and pair stats |
| **GeckoTerminal** | Public DEX pool / OHLCV-style series for on-chain markets |
| **Google Trends** | Search-interest series — the search leg of social arbitrage |

If a pair or topic is absent from these sources, the honest output is **not listed / DARK**, not a generated candle.

### Optional / paid (keyed, licensed, or both)

Bring-your-own key in a **private** environment. Do not commit the key. Do not ask maintainers to paste theirs.

| Source | What it unlocks |
| --- | --- |
| **Helius** | Solana RPC and richer on-chain reads — wallet-level *possibility* when a key exists |
| **Birdeye** | Token-level market analytics (often Solana/EVM screens) beyond a thin public pair list |
| **Nansen** | Wallet labels and smart-money-style attribution — gated, easy to misuse |
| **Arkham** | Entity / wallet intelligence — gated; treat as PII-adjacent |
| **CryptoQuant** | Exchange-flow and related on-chain/CEX metrics — gated |
| **Glassnode** | Broader on-chain indicator sets — gated |
| **Tiingo** | Paid market / news / fundamentals-style coverage; relevant to a **future equities sidecar** |
| **IBKR** | Broker connectivity and a fuller equity/options path — **sidecar, paper-first, Sentinel still on** |

Other vendors will look like these rows: a **port**, an **adapter**, a **mock**, a **DARK path**. Open an issue before adding a new name so we do not collect logos for sport.

### Intentionally blank (DARK until proven)

Do not fill these with fiction:

- Any wallet cluster you cannot cite from a keyed adapter or a public, license-clean source
- SIP-quality US equity prints
- Options unusual-flow narratives
- “Whale bought” without a wallet source
- Synthetic OHLCV used as if it printed

Unknown is a first-class state. **DARK** is more useful than a pretty chart.

## How contributors can help

You do not need a Nansen seat to be useful.

1. **Adapters behind interfaces**  
   Implement one port (`Tape`, `SearchInterest`, …) for one vendor. Accept config from the environment. If the key is absent, return DARK — do not crash the desk, do not fill zeros that look like prices.

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
- **Sentinel stays on.** Community PRs that add a live `create_order` path without a hard paper default will be rejected.
- **Vendor terms.** Scraping around a paywall or sharing a login is not a contribution.

```
# local only — example names, not a real inventory
#   cp .env.example .env
#   # put keys in .env; .env is gitignored

COINGECKO_DEMO_KEY=   # optional even for "free" tiers
HELIUS_API_KEY=       # optional / paid
# do not add a line that is a live secret and then commit it
```

`.env.example` may list **names** of variables. It must not list values.

## What maintainers will never ask you for

- Your exchange password or 2FA
- A production wallet seed
- A dump of the private helix-cx repo
- Permission to “just run live once to see”

If a person claiming to be a maintainer asks for those, it is not part of this community process.
