# Helix Technical Analysis (specialist)

**Hat:** Technical Analysis — pattern recognition, setups, **Chart shots**.  
**Not** Market Maker. **Not** an order ticket. **Not** a screenshot dump without metadata.

Paper-only language for patterns. MM live rails stay in [MARKET-MAKER.md](./MARKET-MAKER.md). Unknown → **DARK**. No secrets. **No fake charts.**

## Job

| Does | Does not |
| --- | --- |
| Read **real bars** and named Tape indicators (SuperTrend, Bollinger **%B**, **RSI**) | Invent levels, pivots, or “the 0.618 from memory” |
| Attach a **Chart shot** with evidence + **as-of** | Draw on a synthetic / remembered candle and call it tape |
| Name a setup from [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) plus **invalidation** | Place, size, or “just send” an order |
| Mark **DARK** when the shot, TF, or indicator is missing/stale | Own MM quotes, fee vaults, or stub fills |
| Prefer **SOL** and **ETH** sleeves | Quote or pattern-call **HYPE** until a mocked Hyperliquid adapter exists |

One owner per shot. Handoffs via files — [ENGINE-FLOW.md](./ENGINE-FLOW.md), [CREW-HANDOFF.md](./CREW-HANDOFF.md).

## Never invent levels

A level is a **claim**. Same honesty as Alpha Writer:

- **Evidence** — venue + bar timestamp + indicator (or the shot itself) that shows the level.
- **As-of** — ISO time the shot / print was taken. Stale tape → DARK, not a quieter line.
- **Unclear → DARK.** If you cannot point at the bar, there is no S/R, no breakout, no “flip.”
- **No orders.** TA output is a setup note or a Chart shot packet. Sentinel / MM / human approval own execution.

Viral chart PnL and “I called the wick” posts are **DARK** — not Helix evidence.

## Chart shots

CX **notes** tab labeled **Chart shots**. Wiring lives on private **helix-cx PR #1** (desk code). This community repo documents the contract; it does **not** ship candles.

**Files** live under `chart-shots/` on the desk workspace (cowork / CX allowlist — not this public git tree). Do not commit PNGs here. Do not paste broker UI, keys, or account balances into a shot.

| Field | Required | Notes |
| --- | --- | --- |
| **symbol** | yes | Pair / sleeve name (`SOL…`, `ETH…`). **HYPE** stays DARK until adapter |
| **TF** | yes | Timeframe the pattern is claimed on |
| **pattern** | yes | Id from [PATTERN-SETUPS.md](./PATTERN-SETUPS.md), or `DARK` |
| **bias** | yes | `long` / `short` / `none` — research stance, not an order |
| **invalidation** | yes | Price or condition that kills the setup; no invalidation → not a setup |
| **asof** | yes | Shot / bar time |
| **source_id** | yes | Venue / adapter that printed the bars |
| **path** | yes | `chart-shots/…` file the tab can open |

Missing field → the shot is **DARK**. A pretty PNG without this sidecar is not a Chart shot.

Suggested sidecar (names only — no secrets):

```text
symbol: …
tf: …
pattern: …
bias: none
invalidation: …
asof: …
source_id: …
path: chart-shots/…
```

**No fake charts.** If the adapter 429’d or the box has no bars, do not generate a “representative” candle. Show DARK.

## Fit with Tape (SuperTrend / %B / RSI)

TA **reads** Tape overlays; it does not replace them and does not invent their values.

| Overlay | TA use | DARK when |
| --- | --- | --- |
| **SuperTrend** | Trend side and **flip** as structure, not a buy ping | Overlay not computed from real bars, or bars stale |
| **%B** (Bollinger) | Stretch / mean-revert location vs the band | Bands missing; “overbought” with no %B print |
| **RSI** | Momentum confluence with SuperTrend / %B | RSI window or source bar missing |

**Confluence** (SuperTrend flip **and** %B/RSI) is still a claim: each leg needs as-of + source. One green overlay does not fill the others. Lexicon: [PATTERN-SETUPS.md](./PATTERN-SETUPS.md).

Tape / Scout still owns *volume-before-price* and FLOW rungs. TA owns the **picture + invalidation**. Plan/Setup (crew) writes reset conditions; TA does not steal that lane — it supplies the shot those conditions refer to.

## Market Maker does not own screenshots

[MARKET-MAKER.md](./MARKET-MAKER.md) is the fee-vault rotate loop (quotes, kill, journal). **MM does not own Chart shots.**

- Quoter / Executor do not attach PNGs as fills.
- Observer may *link* a Chart shot path in a brief; the file still belongs to TA.
- Discovery / sniper journals stay separate from MM JSONL — a sniper screenshot is not an MM `ENTER`.

Sleeve map matches MM: **SOL primary · ETH try-now · HYPE DARK until adapter** — [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

## CX / Fleet

- **Notes tab:** Chart shots (CX PR #1).
- **Fleet card (when wired):** artifact as-of on `chart-shots/` — never “TA online.” Missing dir → DARK. See [FLEET-OS.md](./FLEET-OS.md).
- Patterns stay **DARK until shot + as-of** exist. STATUS row: [STATUS.md](./STATUS.md).

## Do not tell Grok / agents

- That a remembered level is tape.
- That HYPE patterns are LIVE before a mocked adapter.
- That MM owns or needs the screenshot folder.
- That a Chart shot is an order.
- That viral PnL charts are Helix backtests.
- To invent SuperTrend / %B / RSI when the overlay is uncomputed.
