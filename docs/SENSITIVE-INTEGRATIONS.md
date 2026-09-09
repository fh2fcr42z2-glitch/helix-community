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

Helix keeps a **living Free Market Data Scout**: a dedicated hat (person or rotation) whose job is to **keep cataloging**. This page is the public snapshot. The inventory **continues** — vendors change tiers, geos start returning 451, “free” dashboards stay delayed. When that happens, patch *this* file. Do not freeze a stale class because last week’s NOTE used it.

The job is classification, not collection of logins. **Named ≠ wired.** An entry in Top-to-add is a research lead, not an adapter in Helix.

| The Scout does | The Scout does not |
| --- | --- |
| Keep the inventory moving: **FREE**, **FREE-TIER**, **PAID**, or **DARK** | Invent a bar, a whale, a bridge, or a greek to fill a hole |
| Separate **FREE in Helix now** from **Top-to-add** | Treat a delayed dashboard as a live API |
| Cite public vendor docs and public GitHub shells | Paste Bearer tokens, cookies, or `.env` values |
| Prefer the already-free Helix stack for crypto-first CX | Wire Unusual Whales or Theta Data as if they were Coinbase |
| File adapter issues with **mocked tests** | Ask anyone for a key “just to try” |
| Mark wallets / bridges / entity labels **DARK** until a *verified free* source exists | Infer labels from Alchemy, TVL, or a DEX screenshot |

Paper-only. Not a broker. Not financial advice. If a vendor changes a tier, open a docs PR — that *is* Scout work.

### Classification vocabulary

| Class | Meaning on this bench |
| --- | --- |
| **FREE** | Public / keyless endpoint, within vendor terms and rate limits. Default crypto desk. |
| **FREE-TIER** | Signup, demo/RPC key, **delay** (dashboard or ~1y EOD), or a public venue that may 451/403. Useful, **not** a firehose. DARK when the window or geo does not cover the question. |
| **PAID** | Subscription or API credential (often a Bearer token) in a *private* environment. **DARK here** until a read-only key exists privately *and* an adapter + mock exists. |
| **DARK** | Not observed, not licensed, not crypto-first, or unpaid. Do not interpolate. |

A **FREE-TIER dashboard** is not a **FREE API**. A **PAID API** is not on because a landing page exists.

### Capability categories

Every catalog row belongs to one (or more) of these. Crypto-first CX does not owe every category a live feed.

| Category | What the desk is asking | Crypto-first default |
| --- | --- | --- |
| **Spot / perp tape** | What printed, on which venue | **Spot FREE in Helix now** (Coinbase, Kraken). Perp tape is **Top-to-add** (Binance/Bybit/Hyperliquid public) — still **DARK** until an adapter + mock exists; geo 451/403 stays DARK |
| **On-chain TVL / DEX** | Chain stables, TVL, DEX volume, pair stats | **FREE in Helix now** (DefiLlama free, DEX Screener, GeckoTerminal). Bridges/labels still **DARK** |
| **Funding / OI** | Perp funding, open interest, liquidations | **DARK in Helix now.** Public perp venues are Top-to-add; Coinglass Pro is wishlist **PAID** |
| **Whale / flow** | Labeled wallets, CEX entity flow, “unusual” prints | **DARK** without a *verified free* source. UW API is **PAID**+Bearer |
| **Options / greeks** | Options prints and greeks | **Deribit public** = crypto options **Top-to-add**. **Theta Data** = equity sidecar, **not crypto** (FREE-TIER delayed EOD; intraday/Greeks **PAID**) |
| **Sentiment** | Search interest and public chatter | **FREE in Helix now:** Google Trends. **Fear & Greed** is Top-to-add. Social firehoses otherwise **DARK** |

### Catalog (Scout findings — living)

**FREE in Helix now** (crypto-first default desk — public/keyless, already the community baseline):

| Source | Categories | Class | Honest note |
| --- | --- | --- | --- |
| **Coinbase** | Spot tape | **FREE** | Public CEX spot prints and product metadata. Not perps-as-tape unless a separate adapter says so |
| **Kraken** | Spot tape | **FREE** | Second public CEX tape for cross-check (including the ≥25 bp kill switch) |
| **CoinGecko** | Spot tape (aggregated), universe | **FREE** | Caps, identity, public prices — not a matching engine |
| **DefiLlama (free API)** | On-chain TVL / DEX | **FREE** | Stables, TVL, DEX volume aggregates. **Not** bridge netflow, **not** wallets |
| **DEX Screener** | On-chain TVL / DEX | **FREE** | Public pair stats / liquidity. Not labeled whales |
| **GeckoTerminal** | On-chain TVL / DEX, spot-like DEX OHLCV | **FREE** | Public pool series. Thin liquidity still trips a kill switch |
| **Google Trends** | Sentiment | **FREE** | Search-interest leg. Coarse, delayed, still citable |

**Top-to-add** (public or free-tier leads — **not** Helix adapters until a PR with mocks lands). Inventory continues; this list will grow and shrink.

| Source | Categories | Class | Honest note |
| --- | --- | --- | --- |
| **Binance public** | Spot / perp tape, funding/OI | **FREE** *if* the public REST/WS answers | **Geo may 451/403.** On block, the field is **DARK** — do not backfill from CoinGecko |
| **Bybit public** | Spot / perp tape, funding/OI | **FREE** *if* the public REST/WS answers | Same geo caveat as Binance. 451/403 = DARK, not a synthetic perp |
| **Deribit public** | Crypto options | **FREE** public options (crypto) | Not Theta. Not equity. Not greeks-from-nowhere. Adapter + mocks before it is “in Helix” |
| **Hyperliquid** | Perp tape / DEX | **FREE** public perp DEX (typical) | Cite the public API / [python SDK](https://github.com/hyperliquid-dex/hyperliquid-python-sdk). Still DARK in Helix until mocked |
| **Fear & Greed** | Sentiment | **FREE** public index (typical) | One number, not chatter. Do not treat it as the social leg |
| **FRED** | Macro (equity/macro sidecar) | **FREE-TIER** (API key often required, no paywall) | **Not crypto tape.** Sidecar context only |
| **EDGAR** | Filings (equity sidecar) | **FREE** public SEC filings | **Not crypto.** Not a whale feed |
| **Alchemy free tier** | On-chain RPC | **FREE-TIER**, **`eth_call` only** | Read-only contract calls. **Not** `eth_send*`, **not** entity labels, **not** bridges. Labels stay **DARK** |
| **News RSS** | Sentiment / chatter | **FREE** public feeds (typical) | Headlines, not a paid firehose. Cite the feed; do not scrape a paywall. Not wallet flow |
| **PoR seeds** | Venue solvency context | **FREE** *if* the exchange publishes a public Proof-of-Reserves attestation | A published merkle/attestation page is not a wallet cluster. Missing PoR = **DARK**, not “insolvent” |
| **OFAC seeds** | Public sanctions lists | **FREE** public Treasury SDN (and similar published lists) | Research seed only — not a compliance product, not live blocking, not a smart-money label |

**Do not confuse these with FREE firehoses:**

| Source | Categories | Class | Honest note |
| --- | --- | --- | --- |
| **Unusual Whales** | Whale / flow; crypto OHLC via **API** | Free dashboard = **delayed FREE-TIER**. API = **PAID + Bearer only** | The free dashboard is **delayed**. It is **not** a firehose and **not** Coinbase/Kraken. The **API is paid** and authenticates with a **Bearer token** in a *private* env. Without that key, UW is **DARK**. Never paste the Bearer |
| **Theta Data** | Equity / options / indices | **Not crypto.** **FREE-TIER:** ~**1y EOD delayed**. **PAID:** intraday and Greeks | Equity sidecar only. Delayed EOD is not live greeks, not SIP, not a crypto perp or Deribit options tape. Using Theta as if it were Coinbase or Deribit is a bug |

**Wallets, bridges, and entity labels** stay **DARK** until a *verified free* source exists — including after Alchemy **`eth_call`**, DefiLlama TVL, or a DEX screenshot. Paid labels (Nansen, Arkham, GMGN, Helius keyed, UW API) do not change that rule on this public bench. **PoR** and **OFAC** seeds are public lists/attestations, not wallet intelligence products.

### Geo egress honesty

“Public API” is not “reachable from every laptop and every CI.” Binance/Bybit-class venues **may 451/403** by geo or egress policy.

| Rule | Honest behavior |
| --- | --- |
| Record the status | 200 vs 451/403 is part of the observation |
| DARK on block | Do not backfill from CoinGecko, a delayed UW dashboard, or a synthetic perp |
| Do not assume Helix geo | Community CI, GitHub Pages, and your home IP are different egress. A feed that works for you can be DARK in CI |
| Cite shells, don’t fake reach | [ccxt/ccxt](https://github.com/ccxt/ccxt) and [nirholas/crypto-data-aggregator](https://github.com/nirholas/crypto-data-aggregator) are shapes for adapters — still mock; still DARK on 451 |

Cowork notes must write the egress outcome. INVENTORY must not upgrade a geo-blocked venue to FREE-in-Helix-now.

### GitHub shells worth citing

Public repos the Scout can point at when proposing an adapter. **Citing ≠ shipping.** Check their licenses. Do not copy secrets from their issues. Do not treat examples as Helix.

| Shell | Why cite it |
| --- | --- |
| [ccxt/ccxt](https://github.com/ccxt/ccxt) | Venue-shaped public CEX/DEX clients (Binance/Bybit/Deribit class). Still mock in CI; still DARK on 451/403 |
| [nirholas/crypto-data-aggregator](https://github.com/nirholas/crypto-data-aggregator) | Aggregation patterns for multi-venue crypto data |
| [eliasfire617/crypto-market-data-mcp](https://github.com/eliasfire617/crypto-market-data-mcp) | MCP-shaped market-data surface — interface ideas, not a key vault |
| [aitrading-bot/nestor](https://github.com/aitrading-bot/nestor) | Bot/data-plumbing patterns; **paper-only here** — no live-order copy |
| [visioneth/AlphaScope](https://github.com/visioneth/AlphaScope) | Research-scope layout for market context |
| [hyperliquid-dex/hyperliquid-python-sdk](https://github.com/hyperliquid-dex/hyperliquid-python-sdk) | Official-class Hyperliquid python client for a future mocked adapter |

Cowork + Scout should **keep citing these same shells** when proposing ETL, RSS ingest, or Hyperliquid/ccxt-shaped tape — not a new secret gist. **Citing ≠ shipping.**

### Wishlist — research unlocks (one line each)

Paid *or* public-but-unwired. Unpaid/unverified = **DARK**. Swap/trading connectors stay **off**. **DuckDB / SQL warehouse is off-by-default** ([DATA-AND-MEMORY.md](DATA-AND-MEMORY.md)).

| Source | One-line unlock |
| --- | --- |
| **Helius** | Solana RPC / richer on-chain reads — wallet *possibility* with a read-only key |
| **Nansen** | Labeled wallets / smart-money-style attribution |
| **Arkham** | Entity / wallet intelligence (PII-adjacent) |
| **Unusual Whales API** | Crypto whale prints + OHLC. **PAID + Bearer only.** Delayed free dashboard ≠ this row |
| **Glassnode** | Broader on-chain indicator set |
| **CryptoQuant** | CEX entity flow / exchange metrics |
| **Coinglass Pro** | Perp funding, OI, liquidation aggregates |
| **DefiLlama Pro** | Bridge netflow and other Pro-only FLOW |
| **Birdeye** | Token-level analytics / possible wallet reads |
| **GMGN** | Labeled-wallet style screens |
| **Tiingo** | Equities/news-style paid coverage — sidecar, not crypto tape |
| **News RSS (public)** | Headline ingest for the chatter/search gap — not a paid newswire; mocks required |
| **PoR seeds** | Public Proof-of-Reserves attestations as context — not labeled wallets |
| **OFAC seeds** | Public SDN (and similar) as a research seed — not a live compliance engine, not smart money |
| **Alchemy `eth_call` only** | FREE-TIER read-only calls — never send, never treat as labels |

### How the community helps the Scout

**Contributor rule:** propose adapters with **mocks**; **never paste keys**.

1. **Propose an adapter** with **mocked tests** — one vendor, one category. DARK when unkeyed, geo-blocked (451/403), or out of the free window. CI must not need your laptop.
2. **Keep the living catalog moving** — FREE in Helix now vs Top-to-add vs PAID vs DARK. Cite a public page or a GitHub shell, not a screenshot of a key.
3. **Never paste keys** into issues, PRs, or chat. Unusual Whales Bearer tokens, Theta logins, Alchemy keys, Coinglass Pro keys stay in local `.env` (gitignored) or nowhere.
4. **Do not scrape** a delayed dashboard (UW free, Theta delayed EOD) to impersonate a paid or live API.
5. **Do not “unlock” wallets, bridges, or entity labels** without a verified free source. Alchemy **`eth_call`** does not count. PoR/OFAC seeds are lists/attestations, not Nansen.
6. **Geo egress honesty** — 451/403 is DARK. Do not invent a bar because ccxt has a Binance class.

Adapter issue template: label **FREE / FREE-TIER / PAID / DARK** and a capability category. See [CONTRIBUTING.md](CONTRIBUTING.md). SQL warehouse (DuckDB **off-by-default**) / Parquet / prompt discipline / research risk gates (WF, DSR, Kelly): [DATA-AND-MEMORY.md](DATA-AND-MEMORY.md).

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
| **Labeled wallets / entity labels** | Nansen, Arkham, GMGN, Helius keyed, UW API | **DARK** until a *verified free* source exists. Alchemy **`eth_call` ≠ labels**. PoR/OFAC seeds ≠ Nansen |
| **Bridge netflow** | DefiLlama **Pro** | Free Llama is chain stables + TVL + DEX vol only ([FLOW.md](FLOW.md)). **DARK** without verified free |
| **Geo-blocked public tape** | Binance/Bybit-class 451/403 | **DARK**. Do not backfill. Record egress |
| **CEX entity flow** | CryptoQuant, Glassnode **unpaid** | No implied exchange whales |
| **Unusual Whales API** | **PAID + Bearer only** | Delayed free dashboard ≠ API; **DARK** without key |
| **Funding / OI (in Helix now)** | Not wired; Binance/Bybit/Hyperliquid are Top-to-add | **DARK** until adapter + mock; 451/403 = DARK |
| **Theta Data as crypto** | US stocks/options/indices only | Never a crypto tape. **FREE-TIER ~1y EOD delayed**; **intraday/Greeks PAID** |
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

Theta Data is **not crypto**. **FREE-TIER:** about **one year of delayed EOD** equity/options. **PAID:** intraday and Greeks. Listed here so it is not filed as a Coinbase- or Deribit-class FREE tape.

| Source | What it unlocks |
| --- | --- |
| **Unusual Whales API** | Crypto whale prints and OHLC — **PAID + Bearer only**. Delayed free dashboard is **not** this unlock |
| **Theta Data** | Equity/options/indices. **~1y EOD delayed FREE-TIER**; **intraday/Greeks PAID**. **Not crypto** |
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
- Theta Data bars used on a crypto FLOW rung (or as Deribit)
- Funding/OI invented from spot tape or filled in after a 451/403
- Wallet, bridge, or entity labels inferred from Alchemy, TVL, or a screener

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
THETA_DATA_API_KEY=    # optional; ~1y EOD delayed equity sidecar — not crypto; Greeks paid
ALCHEMY_API_KEY=       # optional free-tier RPC; not labels
FRED_API_KEY=          # optional free-tier macro sidecar
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
