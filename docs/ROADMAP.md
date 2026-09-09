---
layout: default
title: Roadmap
permalink: /roadmap/
nav: roadmap
---

# Public roadmap

This is the community north star. It is not a vendor timeline and not a promise that the private build is already here.

Helix stays a **research desk**. Bars get more real. Validation gets harder. Execution stays paper.

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

## Wallet-level data when keys are available

Wallet identity and smart-money labels stay **optional**.

- No key → those ports return DARK. The free desk (tape + Trends + chatter) still runs.
- Key present in a *private* environment → adapters may attach to intake. Book and Sentinel rules do not change.
- Community CI never requires those keys.

Do not design a Scout that *only* works if Nansen is present. Design a Scout that gets sharper if a wallet port is non-DARK.

## Sentinel-gated execution, forever paper-first

This bar does not move to “live when ready.”

- Default path is paper. Always.
- Sentinel blocks unsupervised order entry in community code.
- A future private broker or CEX adapter does not flip the public stance.
- Docs and UI copy say **paper** until a human, outside this community repo, takes a responsibility we will not take here.

If you want Helix to “just send the order,” this is the wrong community. Write a better paper process instead.

## Near / later (honest buckets)

**Near (community-shaped)**

- Document ports and DARK behavior
- Free-tier adapters with mocks (Coinbase, Kraken, CoinGecko, DefiLlama, DEX Screener, GeckoTerminal, Trends)
- Paper thesis template used in issues
- Hunt and delete synthetic defaults

**Later (needs Lab / Fleet, still paper)**

- Walk-forward harness
- Isolated Fleet runs that cannot write the main book
- Alpha Writer publish format
- Equities sidecar **interfaces** (Tiingo / IBKR as optional ports) — not a live equity desk

**Not a goal**

- Public live trading
- Selling signals
- Pretending DARK data is filled in
- Copying helix-cx into this repo

## How to push a bar forward

Open an issue with one of: `adapter`, `paper-idea`, `docs`. Point at the roadmap line you are moving. See [CONTRIBUTING.md](CONTRIBUTING.md).
