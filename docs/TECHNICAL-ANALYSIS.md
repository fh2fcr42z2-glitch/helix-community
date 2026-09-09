# Helix Technical Analysis (specialist)

**Hat:** Technical Analysis — pattern recognition, setups, **Chart shots**.  
**Not** Market Maker. **Not** an order ticket. **Not** a screenshot dump without metadata.

Paper-only language for patterns. MM live rails stay in [MARKET-MAKER.md](./MARKET-MAKER.md). Unknown → **DARK**. No secrets. **No fake charts.**

**TA critique pack = PASS** (doctrine). First SOL/ETH Chart shot pack is **sketch** only (TradingView guest = candles+volume; SuperTrend/%B/RSI/VWAP **DARK**) — not `setup` / not `confluent`. Desk truth: [STATUS.md](./STATUS.md).

## Job

| Does | Does not |
| --- | --- |
| Read **real bars** and named Tape indicators (SuperTrend, Bollinger **%B**, **RSI**, VWAP, ATR) | Invent levels, pivots, or “the 0.618 from memory” |
| Attach a **Chart shot** with sidecar JSON (evidence + **as-of**) | Draw on a synthetic / remembered candle and call it tape |
| Name a `pattern_id` from [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) plus **invalidation** | Place, size, or “just send” an order |
| Grade `setup_grade` honestly; **DARK metadata** if the sidecar is missing | Own MM quotes, fee vaults, or stub fills |
| Prefer **SOL** and **ETH** sleeves | Quote or pattern-call **HYPE** until a mocked Hyperliquid adapter exists |

One owner per shot. Handoffs via files — [ENGINE-FLOW.md](./ENGINE-FLOW.md), [CREW-HANDOFF.md](./CREW-HANDOFF.md).

## Critique pack (PASS) — doctrine

The desk **TA critique** concluded **PASS**. That pack is the assumption source. This community repo **summarizes the contract**; it does not ship helix-cowork files.

| Pointer | Honest note |
| --- | --- |
| **Conceptual path** | Desk box `helix-cowork` TA critique pack (briefs/notes). **May be unmounted** on a Cloud Agent or clone |
| **Public contract** | This page + [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) + Chart shots sidecar below |
| **If the pack file is missing** | Do not invent a gist. Use these pages. Numeric ATR windows you cannot cite stay unlabeled — do not retune |

Treat the pins as **frozen** until a later critique **re-PASSes**. Silent retunes are a bug.

### ASSUMPTION pins

| Pin | Value | Meaning |
| --- | --- | --- |
| **Pivot N** | **2** | Swing high/low: 2 bars left **and** 2 bars right. Do not switch to N=3 “because it looked cleaner” |
| **VWAP** | **UTC day** | Session VWAP resets **00:00 UTC**, not NY, not venue cash session |
| **ATR compress** | **pack defaults** | Compression vs expansion uses the critique’s pinned ATR window/threshold. **Do not retune on the shot.** If you cannot cite the pack numbers, do not invent a length — ATR claims cannot be `confluent` |
| **BOS alone** | **≠ confluent** | A break of structure by itself is at most `setup` (often `sketch`). `bos_retest` needs the **retest**. `setup_grade=confluent` needs an independent second leg |

## Never invent levels

A level is a **claim**. Same honesty as Alpha Writer:

- **Evidence** — venue + bar timestamp + indicator (or the shot itself) that shows the level.
- **As-of** — ISO time the shot / print was taken. Stale tape → DARK, not a quieter line.
- **Unclear → DARK.** If you cannot point at the bar, there is no S/R, no BOS, no “flip.”
- **No orders.** TA output is a setup note or a Chart shot packet. Sentinel / MM / human approval own execution.

Viral chart PnL and “I called the wick” posts are **DARK** — not Helix evidence. **Hype PnL** is a **reject**.

## Chart shots

CX **notes** tab labeled **Chart shots**. Wiring lives on private **helix-cx PR #1** (desk code). This community repo documents the contract; it does **not** ship candles.

**Files** live under `helix-cowork/chart-shots/` on the desk workspace (cowork / CX allowlist — **may be unmounted**; not this public git tree). Sidecar sits next to the image: `chart-shots/<stem>.json` (same stem as the PNG/WebP). Do not commit PNGs here. Do not paste broker UI, keys, or account balances into a shot. Do not invent a chart if the dir is missing.

**Missing sidecar → DARK metadata.** A pretty PNG without JSON is not a Chart shot. Grade is not `setup` or `confluent`. The tab may still list the file; the contract is DARK until the sidecar exists.

### `pattern_id` enum

Exactly one. Canonical list: [PATTERN-SETUPS.md](./PATTERN-SETUPS.md).

`range_fade_sr` · `trend_pullback_vwap` · `rsi_failure_swing` · `bos_retest` · `atr_compress_expand` · `dark_discretionary`

Unknown / mixed / “looks like ICT” → `dark_discretionary`, not a new id.

### `setup_grade`

| Grade | Meaning | May promote? |
| --- | --- | --- |
| **sketch** | Idea; incomplete evidence; pin or overlay missing | No — cowork scrap only |
| **setup** | Shot + sidecar + `pattern_id` + invalidation + as-of + source | Research yes; not “cleared confluence” |
| **confluent** | `setup` **plus** an independent second leg (overlay or structure). **BOS alone ≠ confluent** | Yes, still not an order |
| **reject** | Hits a reject rule below | Stop. Named criterion. Do not re-queue without new evidence |

### Sidecar JSON schema

Required fields. No secrets. No PnL fields.

```json
{
  "symbol": "SOL-USD",
  "tf": "1h",
  "pattern_id": "bos_retest",
  "bias": "none",
  "invalidation": "close back through broken level on 1h",
  "asof": "2026-09-09T00:00:00Z",
  "source_id": "coinbase",
  "path": "chart-shots/sol-usd_1h_2026-09-09.png",
  "setup_grade": "setup",
  "assumption_pins": {
    "pivot_n": 2,
    "vwap_session": "utc_day",
    "atr_compress": "pack_defaults",
    "bos_alone_confluent": false
  }
}
```

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| **symbol** | string | yes | Pair / sleeve (`SOL…`, `ETH…`). **HYPE** → reject until adapter |
| **tf** | string | yes | Timeframe the pattern is claimed on (real bars, one TF per claim) |
| **pattern_id** | enum | yes | See enum above |
| **bias** | `long` \| `short` \| `none` | yes | Research stance, not an order |
| **invalidation** | string | yes | Price or condition that kills the setup |
| **asof** | ISO-8601 | yes | Shot / bar time |
| **source_id** | string | yes | Venue / adapter that printed the bars |
| **path** | string | yes | `chart-shots/…` file the tab can open |
| **setup_grade** | `sketch` \| `setup` \| `confluent` \| `reject` | yes | Missing sidecar ⇒ treat metadata as **DARK** (do not invent `setup`) |
| **assumption_pins** | object | yes | Must echo the pins (pivot_n=2, vwap_session=`utc_day`, atr_compress=`pack_defaults`, bos_alone_confluent=false) |

Wrong `pattern_id`, missing field, or pins that disagree with doctrine → DARK metadata or **reject**, not a quiet edit.

**No fake charts.** If the adapter 429’d or the box has no bars, do not generate a “representative” candle. Show DARK.

### Reject (first-class)

| Reject | Why |
| --- | --- |
| **Synthetic MTF** | Higher-TF structure mashed from interpolated / synthetic bars, or mixed TFs without a real bar + as-of **per TF** |
| **Hype PnL** | Viral “I banked it” charts, Discord call-outs, unverified bot PnL as evidence |
| **Invisible indicators** | Claiming SuperTrend / %B / RSI / VWAP / ATR / pivots that are **not** on the shot **and** not computed from Tape |
| **HYPE until adapter** | Hyperliquid sleeve DARK until a mocked adapter — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) |

Reject is a completed handoff. Do not re-label as `sketch` to keep the tab busy.

## Fit with Tape (SuperTrend / %B / RSI)

TA **reads** Tape overlays; it does not replace them and does not invent their values.

| Overlay | TA use | DARK when |
| --- | --- | --- |
| **SuperTrend** | Trend side and **flip** as structure, not a buy ping | Overlay not computed from real bars, or bars stale |
| **%B** (Bollinger) | Stretch / mean-revert location vs the band | Bands missing; “overbought” with no %B print |
| **RSI** | Momentum confluence; required for `rsi_failure_swing` | RSI window or source bar missing |
| **VWAP** | UTC-day mean for `trend_pullback_vwap` | Non-UTC session used; VWAP not computed |
| **ATR** | Compress / expand for `atr_compress_expand` | Unpinned window; invented threshold |

**Confluence** is `setup_grade=confluent`: each leg needs as-of + source. One green overlay does not fill the others. **BOS alone ≠ confluent.** Lexicon: [PATTERN-SETUPS.md](./PATTERN-SETUPS.md).

Tape / Scout still owns *volume-before-price* and FLOW rungs. TA owns the **picture + invalidation**. Plan/Setup (crew) writes reset conditions; TA does not steal that lane — it supplies the shot those conditions refer to.

## Market Maker does not own screenshots

[MARKET-MAKER.md](./MARKET-MAKER.md) is the fee-vault rotate loop (quotes, kill, journal). **MM does not own Chart shots.**

- Quoter / Executor do not attach PNGs as fills.
- Observer may *link* a Chart shot path in a brief; the file still belongs to TA.
- Discovery / sniper journals stay separate from MM JSONL — a sniper screenshot is not an MM `ENTER`.

Sleeve map matches MM: **SOL primary · ETH try-now · HYPE DARK until adapter** — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## CX / Fleet

- **Notes tab:** Chart shots (CX PR #1).
- **Fleet card (when wired):** artifact as-of on `helix-cowork/chart-shots/` **and** sidecar presence — never “TA online.” Missing dir or missing sidecar → DARK. See [FLEET-OS.md](./FLEET-OS.md).
- Critique **PASS**; first SOL/ETH pack **sketch** (overlays DARK). CX tab still wiring on PR #1. [STATUS.md](./STATUS.md).

## Do not tell Grok / agents

- That a remembered level is tape.
- That HYPE patterns are LIVE before a mocked adapter.
- That MM owns or needs the screenshot folder.
- That a Chart shot is an order.
- That viral / hype PnL charts are Helix backtests.
- That BOS alone is `confluent`.
- That synthetic MTF is structure.
- To invent SuperTrend / %B / RSI / VWAP / ATR when the overlay is uncomputed or invisible.
- That helix-cowork TA files exist on this clone — summarize from **this** page if the pack is unmounted.
