# Helix pattern setups (starter lexicon)

Concise labels for [Technical Analysis](./TECHNICAL-ANALYSIS.md) and Chart shots.  
**Not a buy list. Not a strategy dump. Viral PnL stays DARK.**

Every setup needs **invalidation**. No invalidation → not a setup → **DARK**.  
Levels and overlays need **evidence + as-of**. Unclear → DARK. No orders. No fake charts.

Sleeves: **SOL / ETH** primary. **HYPE DARK** until a mocked Hyperliquid adapter — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## How to use a row

A Chart shot (or cowork note) names **one** pattern id, **bias** (`long` / `short` / `none`), **TF**, **invalidation**, **asof**, **source_id**. Confluence is extra claims, not a vibe.

Tape overlays TA may read (must be computed from real bars): **SuperTrend**, Bollinger **%B**, **RSI**. Missing overlay → that leg is DARK; do not infer it from the PNG.

## Lexicon

| Id | What it is (Helix) | Evidence (minimum) | Invalidation (required) | DARK when |
| --- | --- | --- | --- | --- |
| **trend-structure** | Higher highs / higher lows (or the inverse) on a named TF | Shot + two marked swings with bar times | A close that breaks the last swing the structure needed | Swings drawn from memory; mixed TFs without saying so |
| **s-r** | Support / resistance as **reacted-to** prices, not round numbers you like | At least two touches on real bars, venue named | A decisive close through the level on that TF (define “decisive” on the shot) | Single touch; “psychological” level with no print |
| **breakout-retest** | Range or S/R break, then a **retest** that holds | Break bar + retest bar, both as-of | Retest fails (close back inside / through the broken level) | Break without retest called “the setup”; thin DEX (kill switch) |
| **failure-swing** | Attempted break that **fails** and returns (bull or bear failure) | The failed break bar + the return, same TF | A close that completes the break the failure denied | Calling every wick a failure swing |
| **range-mean-revert** | Rotation inside a bounded range toward mid / mean | Range high/low from bars + location (**%B** preferred) | Range break (use **breakout-retest**, don’t stretch this id) | No range boundary on the shot; mean from a synthetic mid |
| **supertrend-flip-confluence** | **SuperTrend flip** plus **%B** and/or **RSI** agreement | Each overlay’s value/as-of from Tape, not eyeballed | SuperTrend flips back **or** %B/RSI concurrence fails the rule you wrote | Flip without overlay prints; filling RSI from a screenshot guess |

Pick **one** primary id. If two apply, say so as two claims (verification levels still apply on a NOTE).

## Confluence (SuperTrend + %B / RSI)

Helix does **not** treat a single overlay as a setup.

1. **SuperTrend** — side and flip (structure).
2. **%B** — where price sits in the bands (stretch vs mid).
3. **RSI** — momentum, not “overbought = sell” by slogan.

**supertrend-flip-confluence** requires the flip **and** at least one of %B or RSI, each with source + as-of. If only SuperTrend flipped, say `trend-structure` (or DARK confluence), not the confluence id.

Stale BTC / CB vs Kraken ≥ 25 bp / thin DEX still halt **promotion** — [FLOW.md](./FLOW.md). A pretty confluence on a killed tape is not a cleared setup.

## Invalidation is load-bearing

Write it as a **condition**, not a feeling:

- Price: “close below X on TF Y” (X from the shot, not invented).
- Overlay: “SuperTrend flips against bias on the same TF.”
- Time: “no retest within N bars” — only if N is on the note.

If invalidation would require a wallet, a whale, or unpaid flow, that clause is **DARK** and the setup is not cleared.

## Viral PnL DARK

Public “I banked the breakout” charts, Discord call-outs, and unverified bot PnL are **inspiration for process at most**. They are **not**:

- Helix backtests
- Chart shot evidence
- MM journal fields
- A reason to light HYPE

Same rule as [CREW-HANDOFF.md](./CREW-HANDOFF.md) and [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md).

## Out of scope (starter)

This page does not catalog harmonic patterns, ICT jargon, or a 20-rule playbook. Add a row when the desk has a **shot + as-of + invalidation** worth repeating. Do not grow the lexicon from tweets.

CX wiring: Chart shots tab on helix-cx PR #1. Patterns stay DARK until shot+as-of — [STATUS.md](./STATUS.md).
