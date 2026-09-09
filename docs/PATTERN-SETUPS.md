# Helix pattern setups (lexicon)

Labels for [Technical Analysis](./TECHNICAL-ANALYSIS.md) and Chart shots.  
**Not a buy list. Not a strategy dump. Viral / hype PnL stays DARK — and is a Chart shot `reject`.**

**TA critique pack = PASS.** Pins and `pattern_id` enum below are doctrine. First SOL/ETH pack is **sketch** (not `setup`/`confluent`; overlays DARK) — [STATUS.md](./STATUS.md).

Every setup needs **invalidation**. No invalidation → not a setup → **DARK** / `sketch`.  
Levels and overlays need **evidence + as-of**. Unclear → `dark_discretionary`. No orders. No fake charts.

Sleeves: **SOL / ETH** primary. **HYPE** → **reject** until a mocked Hyperliquid adapter — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## How to use a row

A Chart shot sidecar names **one** `pattern_id`, **bias** (`long` / `short` / `none`), **tf**, **invalidation**, **asof**, **source_id**, **setup_grade**. Confluence is a **grade**, not a second id.

`setup_grade`: `sketch` | `setup` | `confluent` | `reject` — [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md).  
**BOS alone ≠ confluent.** Missing sidecar → **DARK metadata**.

Tape overlays TA may read (must be computed from real bars, or they are **invisible** → reject): **SuperTrend**, Bollinger **%B**, **RSI**, **VWAP (UTC day)**, **ATR** (pack defaults).

## `pattern_id` enum (canonical)

Use these ids in sidecar JSON. Do not invent a seventh.

| `pattern_id` | What it is (Helix) | Evidence (minimum) | Invalidation (required) | DARK / reject when |
| --- | --- | --- | --- | --- |
| **range_fade_sr** | Fade a bounded range at **reacted-to** S/R (not a round number you like) | Range high/low from bars; ≥2 touches; **%B** preferred for location | Decisive close **through** the faded side on that TF (define “decisive” on the shot) | Single touch; synthetic mid; calling a trend “a range” |
| **trend_pullback_vwap** | Pullback toward **UTC-day VWAP** in an established trend | Trend structure (pivot **N=2**) + VWAP overlay from **00:00 UTC** session | Close through VWAP **against** the trend, or structure break (last N=2 swing) | NY/venue VWAP; VWAP invisible; no trend structure |
| **rsi_failure_swing** | RSI + price **failure swing** (attempted break that fails and returns) | Failed break bar + return, **same TF**, RSI print as-of | A close that completes the break the failure denied, **or** RSI makes the denied extreme | Every wick called a failure; RSI guessed from the PNG |
| **bos_retest** | Break of structure **then a retest** that holds | BOS bar + **retest** bar, both as-of; pivots **N=2** | Retest fails (close back through the broken level) | **BOS without retest** billed as the setup; BOS graded `confluent` |
| **atr_compress_expand** | ATR **compression** then **expansion** (pack defaults — do not retune) | ATR overlay from Tape using **pack defaults**; named compress then expand bars | Expansion fails (price/ATR back into the compressed regime you defined) | Invented ATR length; invisible ATR; retune “to fit the shot” |
| **dark_discretionary** | Discretionary / mixed / unclear — **honest DARK** | Shot still needs as-of + source if you keep the PNG | n/a — not a tradeable setup | Using this id to hide a missing enum; attaching hype PnL |

Pick **one** primary `pattern_id`. Two families → two claims (or `dark_discretionary`), not a blended id.

Starter aliases (old names → enum): `s-r` / `range-mean-revert` → `range_fade_sr`; `trend-structure` → structure leg of `trend_pullback_vwap` or `bos_retest`; `failure-swing` → `rsi_failure_swing`; `breakout-retest` → `bos_retest`; `supertrend-flip-confluence` is a **grade** (`confluent` with SuperTrend), not a `pattern_id`.

## ASSUMPTION pins (echo in sidecar)

Same table as [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md):

| Pin | Value |
| --- | --- |
| Pivot N | **2** |
| VWAP | **UTC day** (00:00 UTC reset) |
| ATR compress | **pack defaults** (do not retune; uncited numbers ≠ `confluent`) |
| BOS alone | **≠ confluent** |

Critique pack path is conceptual (`helix-cowork` TA critique). This repo summarizes; the file may be unmounted.

## Confluence

`setup_grade=confluent` needs `setup` **plus** an independent second leg, each with source + as-of. Examples:

- `bos_retest` + UTC VWAP hold (not BOS alone)
- `range_fade_sr` + %B stretch
- `rsi_failure_swing` + SuperTrend still on the failure side
- `trend_pullback_vwap` + RSI not making a new extreme

Helix does **not** treat a single overlay as confluence.

1. **SuperTrend** — side and flip (structure).
2. **%B** — where price sits in the bands.
3. **RSI** — momentum; required on `rsi_failure_swing`.
4. **VWAP** — UTC-day mean; required on `trend_pullback_vwap`.
5. **ATR** — pack-default compress/expand; required on `atr_compress_expand`.

Stale BTC / CB vs Kraken ≥ 25 bp / thin DEX still halt **promotion** — [FLOW.md](./FLOW.md). A pretty confluence on a killed tape is not a cleared setup.

## Invalidation is load-bearing

Write it as a **condition**, not a feeling:

- Price: “close below X on TF Y” (X from the shot, not invented).
- Overlay: “SuperTrend flips against bias on the same TF.”
- VWAP: “UTC-day VWAP lost on a close.”
- Time: “no retest within N bars” — only if N is on the sidecar.

If invalidation would require a wallet, a whale, or unpaid flow, that clause is **DARK** and the setup is not cleared.

## Reject (same list as Chart shots)

- **Synthetic MTF**
- **Hype PnL**
- **Invisible indicators**
- **HYPE until adapter**

Full table: [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md#reject-first-class).

## Out of scope

This page does not catalog harmonic patterns, ICT jargon, or a 20-rule playbook. Do not grow the enum from tweets. A new id needs a later critique **PASS**, not a Discord nickname.

CX wiring: Chart shots tab on helix-cx PR #1. First SOL/ETH pack **sketch**; overlays DARK — [STATUS.md](./STATUS.md).
