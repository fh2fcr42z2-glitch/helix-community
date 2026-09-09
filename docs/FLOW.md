---
layout: default
title: FLOW
permalink: /flow/
nav: flow
---

# Capital-flow hierarchy (FLOW)

Crypto-first Helix CX does not start at a ticker and hope a narrative appears. It **climbs a ladder**. Each rung is allowed to stay **DARK**. You do not invent the next rung to make a chart look finished.

```
Chain   →  DEX   →  token   →  wallets
free       free      board      DARK
Llama      Llama     +          until a *read-only*
stables    volume    trending   research key exists
TVL        + pair
DEX vol    screener
```

This is **FLOW**: where capital *might* be moving, as far as **public, license-clean** data can say. It is not a wallet product. It is not a routing engine. It does not place orders.

Social arbitrage (tape vs search vs chatter) still applies at every rung. FLOW answers *which market you are looking at*. The three legs answer *whether the story agrees with itself*. See [CONCEPT.md](CONCEPT.md).

## Rungs

| Rung | What you may observe on the free desk | What you may not infer |
| --- | --- | --- |
| **Chain** | Stablecoin / TVL / DEX volume aggregates via **DefiLlama (free)** | That “the chain” is a single book, or that TVL is wallet identity |
| **DEX** | **Llama DEX volume** plus a **screener pair** (DEX Screener / GeckoTerminal-class public pair stats) | That pair volume is informed flow, or that a thin pool is a tape |
| **Token** | A **board** (listed/universe) plus **trending** (what the public screens are surfacing) | That trending is smart money, or that a board listing is liquidity |
| **Wallets** | **DARK** | Anything labeled, clustered, or “whale” until a **read-only research key** exists in a *private* environment |

Climb in order. A trending token with no chain and no pair is a headline, not FLOW. A pair with no chain context is a screenshot. Wallets are not a free rung — see [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

### Chain (free)

DefiLlama’s public surface is enough to ask: is this chain’s stables, TVL, or DEX volume doing something that disagrees with the CEX tape or with search? That is a Scout question. It is not a bridge-flow question. **Bridge netflow is DARK** (Llama Pro). Do not back it out from TVL.

### DEX (free)

Two public pieces, kept distinct:

- **Llama volume** — venue/DEX-level volume, not a matching engine.
- **Screener pair** — one pool’s public stats (price, liquidity, advertised volume).

If either piece is missing, label it DARK. Do not average them into a fake “DEX tape.”

### Token (board + trending)

The board is the universe the desk is willing to name. Trending is whatever public screens currently push up. Both can be wrong. Both are still more honest than a hand-picked coin with no board.

A token NOTE must say which board and which trending window, or those fields are DARK.

### Wallets (DARK)

Labeled wallets, clustering, GMGN-style screens, Helius/Birdeye wallet reads — **off the free desk**. They become *possible* only when a **read-only** research key is present privately. Community CI never requires that key. Swap, spend, or trading-session credentials are not research keys; they stay **off**. See [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

## Kill switches (paper desk only)

Kill switches halt **promotion** — Scout → Researcher → paper book → Alpha Writer NOTE. They do **not** send orders. There are no live orders in this community framing.

Public defaults the community should share:

| Switch | Trip | What the desk does |
| --- | --- | --- |
| **Stale BTC** | BTC tape is older than the desk will trust (or freshness is unmeasured) | Pause alt FLOW stories. If you cannot *say* how stale, treat the switch as **on** |
| **Coinbase vs Kraken ≥ 25 bp** | Spot disagreement between those two public CEX tapes is at least **25 basis points** | Do not treat a single venue as “the tape.” Record both prints. Do not promote a NOTE that needs one fair price |
| **Thin DEX liquidity** | Screener pair liquidity is too small to read volume as flow — or liquidity was not measured | Pair FLOW is DARK. Do not dress a thin pool up as chain capital movement |
| **Geo egress 451/403** | Public venue refused this egress (Binance/Bybit class) | Field is **DARK**. Do not backfill. Write the status in cowork notes |

Staleness windows and “how thin is thin” belong in documented config, not magic. Until a number is written down next to a mock test, **unmeasured counts as tripped**.

Market Ops owns the check. Risk may still veto after a switch is clear. Sentinel still forbids live `create_order`. None of these switches are trading signals.

## What FLOW will not pretend

- That DefiLlama TVL is CEX inflow.
- That a screener’s volume column is informed flow.
- That trending tokens have labeled wallets.
- That Unusual Whales’ delayed dashboard is a Coinbase tape, or that Theta Data EOD options are crypto (or Deribit).
- That a Binance/Bybit 451/403 is a hole you may fill from CoinGecko.
- That Alchemy free-tier RPC is wallet labels or bridge netflow.
- That funding/OI exists because spot volume exists.
- That Llama Pro, GMGN, Helius, Birdeye, CryptoQuant, Glassnode, Coinglass Pro, or UW API are on because they appear in a sentence. **Named ≠ wired.** Absent a key and an adapter test, the field is DARK.

Next: headline judge is [READER.md](READER.md) (upstream of Writer). Evidence-gated publication is [ALPHA-WRITER.md](ALPHA-WRITER.md). Adapter rules: [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).
