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

## Free Market Data Scout (charter)

Helix keeps a dedicated **Free Market Data Scout** hat: someone (or a rotation) who **continuously catalogs** market sources for the public bench.

The job is classification, not collection of logins.

| The Scout does | The Scout does not |
| --- | --- |
| Label each source **FREE**, **FREE-TIER**, **PAID**, or **DARK** | Invent a bar, a whale, or a greek to fill a hole |
| Map sources onto capability categories (below) | Treat a delayed dashboard as a live API |
| Cite public vendor docs when a class changes | Paste Bearer tokens, cookies, or `.env` values |
| Prefer the **already-free stack** for crypto-first CX | Wire Unusual Whales or Theta Data as if they were Coinbase |
| File adapter issues with **mocked tests** | Ask anyone for a key “just to try” |

This catalog lives in *this* file. If a vendor changes a tier, open a docs PR. Named ≠ wired. Paper-only. Not a broker. Not financial advice.

### Classification vocabulary

| Class | Meaning on this bench |
| --- | --- |
| **FREE** | Public / keyless endpoint, within vendor terms and rate limits. Default crypto desk. |
| **FREE-TIER** | Signup, demo key, delay, or a short EOD window. Useful, **not** a firehose. Adapters must still DARK when the free window does not cover the question. |
| **PAID** | Subscription or API credential (often a Bearer token) in a *private* environment. **DARK here** until a read-only key exists privately *and* an adapter + mock exists. |
| **DARK** | Not observed, not licensed, not crypto-first, or unpaid. Do not interpolate. |

A **FREE-TIER dashboard** is not a **FREE API**. A **PAID API** is not on because a landing page exists.

### Capability categories

Every catalog row belongs to one (or more) of these. Crypto-first CX does not owe every category a live feed.

| Category | What the desk is asking | Crypto-first default |
| --- | --- | --- |
| **Spot / perp tape** | What printed, on which venue | **Spot FREE** (Coinbase, Kraken). **Perp / funding tape DARK** on the current free stack |
| **On-chain TVL / DEX** | Chain stables, TVL, DEX volume, pair stats | **FREE** (DefiLlama free, DEX Screener, GeckoTerminal) |
| **Funding / OI** | Perp funding, open interest, liquidations | **DARK** unless a named FREE adapter exists; Coinglass Pro is wishlist **PAID** |
| **Whale / flow** | Labeled wallets, CEX entity flow, “unusual” prints | **DARK** without a read-only key |
| **Options / greeks** | Equity/index options, greeks, EOD chains | **Equity sidecar only.** Not crypto. Theta Data is **FREE-TIER** EOD, not a SIP firehose |
| **Sentiment** | Search interest and public chatter | **FREE** for Google Trends; social firehoses otherwise **DARK** |

### Catalog (honest rows)

**Already FREE in the stack** (crypto-first default desk):

| Source | Categories | Class | Honest note |
| --- | --- | --- | --- |
| **Coinbase** | Spot tape | **FREE** | Public CEX spot prints and product metadata. Not perps-as-tape unless a separate adapter says so |
| **Kraken** | Spot tape | **FREE** | Second public CEX tape for cross-check (including the ≥25 bp kill switch) |
| **CoinGecko** | Spot tape (aggregated), universe | **FREE** | Caps, identity, public prices — not a matching engine |
| **DefiLlama (free API)** | On-chain TVL / DEX | **FREE** | Stables, TVL, DEX volume aggregates. **Not** bridge netflow |
| **DEX Screener** | On-chain TVL / DEX | **FREE** | Public pair stats / liquidity. Not labeled whales |
| **GeckoTerminal** | On-chain TVL / DEX, spot-like DEX OHLCV | **FREE** | Public pool series. Thin liquidity still trips a kill switch |
| **Google Trends** | Sentiment | **FREE** | Search-interest leg. Coarse, delayed, still citable |

**Do not confuse these with FREE firehoses:**

| Source | Categories | Class | Honest note |
| --- | --- | --- | --- |
| **Unusual Whales** | Whale / flow; crypto OHLC via **API** | **PAID** for API. Delayed **FREE-TIER** dashboard is **not** the API | Crypto whale prints and OHLC on the **API need a Bearer token** in a private env. The free dashboard is **delayed**. It is **not** a free firehose and **not** a substitute for Coinbase/Kraken tapes. Without the key, UW is **DARK** |
| **Theta Data** | Options / greeks (US stocks, options, indices) | **FREE-TIER** (~30d EOD options) | **Not crypto.** Equity sidecar only. A public window on the order of **~30 days of EOD options** is not live greeks, not SIP, not a crypto perp tape. Using Theta as if it were Coinbase is a bug |

### Wishlist — paid unlocks (one line each)

These are **research reads** someone might bring to a *private* environment. They do not live in this repo. Unpaid = **DARK**. Swap/trading connectors stay **off**.

| Source | One-line unlock |
| --- | --- |
| **Helius** | Solana RPC / richer on-chain reads — wallet *possibility* with a read-only key |
| **Nansen** | Labeled wallets / smart-money-style attribution |
| **Arkham** | Entity / wallet intelligence (PII-adjacent) |
| **Unusual Whales API** | Crypto whale prints + OHLC (Bearer). Delayed free dashboard ≠ this row |
| **Glassnode** | Broader on-chain indicator set |
| **CryptoQuant** | CEX entity flow / exchange metrics |
| **Coinglass Pro** | Perp funding, OI, liquidation aggregates |
| **DefiLlama Pro** | Bridge netflow and other Pro-only FLOW |
| **Birdeye** | Token-level analytics / possible wallet reads |
| **GMGN** | Labeled-wallet style screens |
| **Tiingo** | Equities/news-style paid coverage — sidecar, not crypto tape |

### How the community helps the Scout

1. **Propose an adapter** with **mocked tests** — one vendor, one category, DARK when unkeyed or out of window. CI must not need your laptop.
2. **Correct this catalog** when a vendor’s public docs change a tier. Cite the public page, not a screenshot of a key.
3. **Never paste keys** into issues, PRs, or chat. Unusual Whales Bearer tokens, Theta logins, Coinglass Pro keys, and everything else stay in local `.env` (gitignored) or nowhere.
4. **Do not scrape** a delayed dashboard to impersonate a paid API.

Adapter issue template: label **FREE / FREE-TIER / PAID / DARK** and a capability category. See [CONTRIBUTING.md](CONTRIBUTING.md).

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
| **Unusual Whales API** | Bearer-keyed crypto whales / OHLC | Delayed free dashboard ≠ API; **DARK** without key |
| **Funding / OI** | Not in the FREE stack; Coinglass Pro is wishlist | **DARK** until a named FREE or keyed adapter exists |
| **Theta Data as crypto** | US stocks/options/indices only | Never a crypto tape. Equity sidecar **FREE-TIER** EOD only |
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

Theta Data’s ~30d EOD options window is **FREE-TIER** and **not crypto** — listed here so it is not filed as a Coinbase-class FREE tape.

| Source | What it unlocks |
| --- | --- |
| **Unusual Whales API** | Crypto whale prints and OHLC — **Bearer key** in a private env. Delayed free dashboard is **not** this unlock |
| **Theta Data** | US stocks / options / indices EOD (free window ~30d options). **Not crypto.** Equity sidecar only |
| **Coinglass Pro** | Perp funding, OI, liquidation aggregates — unpaid = **DARK** |
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
- Unusual Whales treated as a free Coinbase replacement
- Theta Data bars used on a crypto FLOW rung
- Funding/OI invented from spot tape

Unknown is a first-class state. **DARK** is more useful than a pretty chart.

### Swap and trading connectors stay off

There is no community port for swaps, CEX orders, routers, or withdraw. Sentinel rejects PRs that add them “for completeness.” IBKR and similar names in the matrix are **not** an invitation to wire a session. Paper book only.

## How contributors can help

You do not need a Nansen seat to be useful.

1. **Adapters behind interfaces**  
   Implement one port (`Tape`, `SearchInterest`, `ChainFlow`, `DexVolume`, `TokenBoard`, …) for one vendor. Accept config from the environment. If the key is absent **or the free window does not cover the query**, return DARK — do not crash the desk, do not fill zeros that look like prices. **Read-only research keys only.** **Mocks in tests** — required to merge.

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
UNUSUAL_WHALES_API_KEY=  # optional Bearer in private env; delayed dashboard ≠ this
THETA_DATA_API_KEY=    # optional; equity sidecar EOD only — not crypto
COINGLASS_API_KEY=     # optional; funding/OI stays DARK if blank
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
