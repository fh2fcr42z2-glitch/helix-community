# Helix Technical Analysis (specialist)

**Hat:** Technical Analysis — pattern recognition, setups, **Chart shots**.  
**Not** Market Maker. **Not** an order ticket. **Not** a screenshot dump without metadata.

Paper-only language for patterns. MM live rails stay in [MARKET-MAKER.md](./MARKET-MAKER.md). Unknown → **DARK**. No secrets. **No fake charts.**

**TA critique pack = PASS** (doctrine). First SOL/ETH Chart shot pack is **sketch** only (TradingView guest = candles+volume; SuperTrend/%B/RSI/VWAP **DARK**) — not `setup` / not `confluent`. Desk truth: [STATUS.md](./STATUS.md).

Public Chart bot contract (readable cards, five-force spine, file-based learning): [CHART-BOT.md](./CHART-BOT.md). Force tags: [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md) · Grok pack: [grok/GROK-ALPHA-FIVE-FORCES.md](./grok/GROK-ALPHA-FIVE-FORCES.md).

## Job

| Does | Does not |
| --- | --- |
| Read **real bars** and named Tape indicators (SuperTrend, Bollinger **%B**, **RSI**, VWAP, ATR) | Invent levels, pivots, or “the 0.618 from memory” |
| Attach a **Chart shot** with sidecar JSON (evidence + **as-of**) | Draw on a synthetic / remembered candle and call it tape |
| Name a `pattern_id` from [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) plus **invalidation** | Place, size, or “just send” an order |
| Grade `setup_grade` honestly; **DARK metadata** if the sidecar is missing | Own MM quotes, fee vaults, or stub fills |
| Put a **five-force spine** on every thesis (`DARK` if unclear) | Invent macro because the candle moved |
| File retros in `ta-learning/` + [PATTERN-EDGE-LOG](../ta-learning/PATTERN-EDGE-LOG.md) | Silent weight magic; viral PnL as a training label |
| Prefer **SOL** and **ETH** sleeves | Quote or pattern-call **HYPE** until a mocked Hyperliquid adapter exists |

One owner per shot. Handoffs via files — [ENGINE-FLOW.md](./ENGINE-FLOW.md), [CREW-HANDOFF.md](./CREW-HANDOFF.md).

## Critique pack (PASS) — doctrine

The desk **TA critique** concluded **PASS**. That pack is the assumption source. This community repo **summarizes the contract**; it does not ship helix-cowork files.

| Pointer | Honest note |
| --- | --- |
| **Conceptual path** | Desk box `helix-cowork` TA critique pack (briefs/notes). **May be unmounted** on a Cloud Agent or clone |
| **Public contract** | This page + [CHART-BOT.md](./CHART-BOT.md) + [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) + Chart shots sidecar below |
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

CX **notes** tab labeled **Chart shots** (Chart bot). Wiring lives on private **helix-cx PR #1** (desk code). This community repo documents the contract; it does **not** ship candles. Humans read the **card**, not the PNG pixels — [Readable Chart shot cards](#readable-chart-shot-cards).

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
  "levels": [
    {
      "name": "broken_level",
      "asof": "2026-09-09T00:00:00Z",
      "evidence": "labeled from the shot; price DARK if not printed on the sidecar"
    }
  ],
  "invalidation": "close back through broken level on 1h",
  "thesis_blurb": "BOS then retest on 1h. Overlays DARK until Tape computes them. Force DARK — no macro invented from the candle.",
  "primary_force": "DARK",
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

Schema illustration only — not a live SOL thesis and not a fabricated macro story. First desk pack remains **sketch**; overlays DARK.

| Field | Type | Required | Notes |
| --- | --- | --- | --- |
| **symbol** | string | yes | Pair / sleeve (`SOL…`, `ETH…`). **HYPE** → reject until adapter |
| **tf** | string | yes | Timeframe the pattern is claimed on (real bars, one TF per claim) |
| **pattern_id** | enum | yes | See enum above |
| **bias** | `long` \| `short` \| `none` | yes | Research stance, not an order |
| **levels** | array | yes | Human-readable S/R / structure from **real bars**. Each item: `name` + `asof` + evidence. Unclear price → omit the number and say DARK — do not invent |
| **invalidation** | string | yes | Price or condition that kills the setup. Humans read this on the card |
| **thesis_blurb** | string | yes | One short English paragraph: what the picture claims. Not a ticker dump, not indicator soup |
| **primary_force** | enum | yes | Dalio spine: `debt_cycle` \| `internal_order` \| `geopolitics` \| `nature` \| `inventiveness` \| `DARK`. **Unclear → `DARK`.** Never invent macro |
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
| **Hype PnL** | Viral “I banked it” charts, Discord call-outs, unverified bot PnL as evidence **or as a learning label** |
| **Invisible indicators** | Claiming SuperTrend / %B / RSI / VWAP / ATR / pivots that are **not** on the shot **and** not computed from Tape |
| **HYPE until adapter** | Hyperliquid sleeve DARK until a mocked adapter — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) |
| **Fabricated macro** | A force tag without evidence; geopolitics because Twitter said “war”; inventiveness because the candle is green |

Reject is a completed handoff. Do not re-label as `sketch` to keep the tab busy.

## Readable Chart shot cards

A Chart shot is a **card humans can read**, not a PNG dump. The CX tab may show the image; the contract is the sidecar fields a person (or Grok) can check without staring at pixels.

| Field humans read | Job | DARK / fail when |
| --- | --- | --- |
| **levels** | Named S/R or structure that actually printed, each with as-of + evidence | Remembered pivots, round numbers you like, prices not on the shot |
| **invalidation** | The condition that kills the thesis, in English a reviewer can test | Vibes (“if it looks weak”); wallet/whale clauses; missing field |
| **thesis_blurb** | One short paragraph: what this picture claims *now* | Indicator soup, ticker spam, a copy-paste from a viral thread |

Missing any of the three → the card is not readable → **DARK metadata**, even if the PNG is pretty. `setup_grade` stays `sketch` (or `reject`) until the card is complete.

Do not hide the thesis in the filename. Do not make the human reverse-engineer SuperTrend from a screenshot. Short public contract: [CHART-BOT.md](./CHART-BOT.md).

## Five-force macro spine

Every Chart-bot thesis carries a **Dalio five-force spine**. The tag answers “which force is actually driving it?” — it is a **label**, not a forecast and not a buy list.

Exact strings (same as the Grok Alpha pack):

`debt_cycle` | `internal_order` | `geopolitics` | `nature` | `inventiveness` | `DARK`

| Chart bot `primary_force` | Alpha Writer tag | Force (plain language) |
| --- | --- | --- |
| `debt_cycle` | `force:credit` | Money, credit, debt, liquidity, leverage |
| `internal_order` | `force:internal` | Domestic politics, policy, social cohesion |
| `geopolitics` | `force:external` | War, sanctions, trade/currency blocs — **no invented wallets** |
| `nature` | `force:nature` | Disaster, pandemic, climate / physical shock |
| `inventiveness` | `force:tech` | Protocol, hardware, model, or market-structure change |
| `DARK` | `force:DARK` | Unclear — **do not guess** |

**Never invent macro.** A dump is not `geopolitics`. A green candle is not `inventiveness`. A coin moving is not `debt_cycle`. If you cannot cite which force, or the force is a vibe, **`primary_force` is `DARK`.**

Same honesty as Alpha Writer: each non-DARK tag needs a claim + verification level + source. Missing source → DARK, not a quieter font. World Monitor stays DARK unpaid — do not paste MCP tokens.

Lens: [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md). Copy-paste Grok pack: [grok/GROK-ALPHA-FIVE-FORCES.md](./grok/GROK-ALPHA-FIVE-FORCES.md). There is **no** private Grok chat dump in this repo.

A Chart shot still needs FLOW / Tape hygiene. Forces do not replace bars.

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

## Learning loop (files, not silent weights)

Chart bot **learns in the open**. After a thesis resolves — invalidated, still standing, or rejected — write a file. Do not quietly retune ATR, pivot N, or overlay weights. Do not hide a “the model updated” in a checkpoint.

| Artifact | Where | Job |
| --- | --- | --- |
| **Retro** | [`ta-learning/`](../ta-learning/) dated notes (template: [`RETRO.template.md`](../ta-learning/RETRO.template.md)) | What was claimed, what printed, whether invalidation hit, force tag, DARK list, what to keep or drop |
| **PATTERN-EDGE-LOG** | [`ta-learning/PATTERN-EDGE-LOG.md`](../ta-learning/PATTERN-EDGE-LOG.md) | Running log of pattern observations. Not a scoreboard. Not a backtest report |

Desk copies may also live under `helix-cowork/ta-learning/` (**may be unmounted**). If the dir is missing, do not invent retros. This repo holds the **public contract + empty log** — no fabricated edges, no fake charts, no fabricated macro.

**Viral PnL is never a training label.** Influencer screenshots, Discord “I called it,” unverified bot PnL, and hype-thread dollar claims do not enter a retro as evidence that a `pattern_id` works. They are already a Chart-shot **reject**. They are also forbidden as fine-tune fuel. Hypothetical paper P&L is not a license to skip walk-forward + DARK list — [RESEARCH-LOOP.md](./RESEARCH-LOOP.md) · [RISK-GATES.md](./RISK-GATES.md).

Stage 6 (fine-tune) for TA = **append a retro and a log row**, with `quality_flag`. Negative results are first-class. Silent weight magic is a bug.

## Market Maker does not own screenshots

[MARKET-MAKER.md](./MARKET-MAKER.md) is the fee-vault rotate loop (quotes, kill, journal). **MM does not own Chart shots.**

- Quoter / Executor do not attach PNGs as fills.
- Observer may *link* a Chart shot path in a brief; the file still belongs to TA.
- Discovery / sniper journals stay separate from MM JSONL — a sniper screenshot is not an MM `ENTER`.

Sleeve map matches MM: **SOL primary · ETH try-now · HYPE DARK until adapter** — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## CX / Fleet

- **Notes tab:** Chart shots / Chart bot (CX tab on helix-cx **PR #1**).
- **Readable card:** `levels` + `invalidation` + `thesis_blurb` on the sidecar — not PNG-only.
- **Fleet card (when wired):** artifact as-of on `helix-cowork/chart-shots/` **and** sidecar presence — never “TA online.” Missing dir or missing sidecar → DARK. See [FLEET-OS.md](./FLEET-OS.md).
- Critique **PASS**; first SOL/ETH pack **sketch** (overlays DARK). CX tab still wiring on PR #1. Learning via `ta-learning/` retros, not weights. [STATUS.md](./STATUS.md) · [CHART-BOT.md](./CHART-BOT.md).

## Do not tell Grok / agents

- That a remembered level is tape.
- That HYPE patterns are LIVE before a mocked adapter.
- That MM owns or needs the screenshot folder.
- That a Chart shot is an order.
- That viral / hype PnL charts are Helix backtests **or training labels**.
- That BOS alone is `confluent`.
- That synthetic MTF is structure.
- To invent SuperTrend / %B / RSI / VWAP / ATR when the overlay is uncomputed or invisible.
- To invent a five-force tag because the coin moved — unclear → **`DARK`**.
- That Chart bot silently updates model weights instead of filing a `ta-learning/` retro.
- That helix-cowork TA files exist on this clone — summarize from **this** page if the pack is unmounted.
