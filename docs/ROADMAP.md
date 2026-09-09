---
layout: default
title: Roadmap
permalink: /roadmap/
nav: roadmap
---

# Public roadmap

This is the community north star. It is not a vendor timeline and not a promise that the private build is already here.

Helix stays a **research desk**. Bars get more real. FLOW stays honest. NOTEs stay evidence-gated. Execution stays paper.

## FLOW on the free bench

Crypto-first CX should be usable with DefiLlama (stables / TVL / DEX vol), Llama volume + screener pair, and a token board + trending — plus public CEX tapes and Trends.

- Wallets stay **DARK** until a read-only research key exists in a private environment.
- Bridge netflow, labeled wallets, unpaid CEX entity flow stay DARK until then.
- Kill switches (stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX liquidity) halt promotion, never live orders.

See [FLOW.md](FLOW.md).

## Real bars everywhere

Every chart, mark, and paper fill should point at a **print that existed**: a public CEX/DEX API, a later licensed tape, or a test fixture labeled as a mock.

- No silent interpolation across a hole in the tape.
- No “representative” candle when the vendor 429’d.
- Timestamps and venue on the bar, or the bar does not ship.

If the adapter cannot get a real bar, the surface shows **DARK** and Process records the miss.

## Kill synthetic data

Synthetic series were a scaffold. They are not a market.

- Remove generators that impersonate OHLCV for the desk UI.
- Keep *simulators* only where they are named as simulations (Lab), never as tape.
- Paper marks that came from a synthesizer are invalid. Re-mark from a real source or close the paper line as data-void.

Community PRs that add a “demo feed” must say `synthetic` in the type name and must be impossible to select as the default tape.

## Walk-forward validation

A thesis that only works on the window you used to write it is a diary entry.

**Lab (future)** should make the boring path the default:

1. Freeze a rule or a question.
2. Train / form the thesis on window A.
3. Score it on later window B that the thesis did not see.
4. Write down what stayed DARK in both windows.

Walk-forward is still **paper**. It does not become a live allocator. Overfit notes are welcome; hidden look-ahead is not.

## Alpha Writer NOTE, no auto-post

A NOTE is the public artifact: Scout → Researcher → Market Ops → Alpha Writer, with claim verification levels.

- **No X auto-post** (stays DARK / off).
- **WordPress is draft-only future** — not live publish, not in this repo’s secrets.
- A NOTE without a DARK list or kill-switch status is not a NOTE.

See [ALPHA-WRITER.md](ALPHA-WRITER.md).

## Wallet-level data when keys are available

Wallet identity and smart-money labels stay **optional** and **read-only**.

- No key → those ports return DARK. The free desk (tape + Trends + chatter) still runs.
- Key present in a *private* environment → adapters may attach to intake. Book and Sentinel rules do not change.
- Community CI never requires those keys.

Do not design a Scout that *only* works if Nansen is present. Design a Scout that gets sharper if a wallet port is non-DARK.

## Sentinel-gated execution, forever paper-first

This bar does not move to “live when ready.”

- Default path is paper. Always.
- Sentinel blocks unsupervised order entry **and** swap/router paths in community code.
- Trading connectors stay **off**. A future private broker name in the matrix does not flip that.
- Docs and UI copy say **paper** until a human, outside this community repo, takes a responsibility we will not take here.

If you want Helix to “just send the order,” this is the wrong community. Write a better paper process instead.

## Near / later (honest buckets)

**Near (community-shaped)**

- Document ports and DARK behavior (including the standing DARK list)
- Keep the **living Free Market Data Scout** catalog moving (FREE in Helix now vs Top-to-add)
- Top-to-add adapters **with mocks**: Binance/Bybit public (DARK on 451/403), Deribit public options, Hyperliquid, Fear & Greed
- Wallets / bridges / entity labels stay **DARK** without a verified free source
- Free-tier FLOW adapters with mocks (DefiLlama chain vol/TVL, Llama+screener DEX, token board/trending, Coinbase, Kraken, Trends)
- Kill-switch tests: stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX — as *promotion halts*
- Paper thesis / NOTE template used in issues
- Hunt and delete synthetic defaults

**Later (needs Lab / Fleet, still paper)**

- Warehouse **quality gates** and ETL that persist DARK instead of inventing ([DATA-AND-MEMORY.md](DATA-AND-MEMORY.md))
- Walk-forward harness
- Isolated Fleet runs that cannot write the main book
- Alpha Writer NOTE format in the wild (still no auto-post)
- WordPress **draft-only** parking, if ever — never live publish from this repo
- Equities sidecar **interfaces** (Tiingo as optional read-only) — not a live equity desk; IBKR is a name only, connectors off

**Not a goal**

- Public live trading or swaps
- X auto-post / signal blasting
- Pretending DARK data is filled in
- Copying helix-cx into this repo

## How to push a bar forward

Open an issue with one of: `adapter`, `paper-idea`, `docs`. Point at the roadmap line you are moving. See [CONTRIBUTING.md](CONTRIBUTING.md).
