# Chart bot (public contract)

Chart bot is the CX **Chart shots** tab plus the **readable card** on every thesis: named levels, invalidation, a short blurb, and a Dalio five-force spine.

Paper-only. Not a signal service. Not financial advice. Not an order ticket.

**No secrets. No fake charts. No fabricated macro.**

Full specialist contract: [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md). Desk truth: [STATUS.md](./STATUS.md). Pattern ids: [PATTERN-SETUPS.md](./PATTERN-SETUPS.md).

## What it is

| Piece | Public truth |
| --- | --- |
| **CX tab** | Chart shots on private **helix-cx PR #1** (desk code). This repo documents; it does not ship candles |
| **Readable card** | Humans read `levels`, `invalidation`, `thesis_blurb` — not PNG pixels |
| **Five-force spine** | Every thesis tagged `debt_cycle` \| `internal_order` \| `geopolitics` \| `nature` \| `inventiveness` \| `DARK` |
| **Learning** | File-based retros in [`ta-learning/`](../ta-learning/) + [PATTERN-EDGE-LOG](../ta-learning/PATTERN-EDGE-LOG.md) |

First SOL/ETH pack on the desk is **sketch** (guest candles+volume; overlays DARK). Do not promote it to `setup` / `confluent` from this page.

## Fields humans read

| Field | Must be |
| --- | --- |
| **levels** | Structure that printed, with as-of + evidence. Unclear → DARK, not a remembered pivot |
| **invalidation** | A testable condition. No invalidation → not a thesis |
| **thesis_blurb** | One short English paragraph. Not indicator soup, not a viral-thread paste |

A pretty PNG without those three is **not** a readable Chart shot. Sidecar JSON is required — missing sidecar → DARK metadata.

## Five-force spine

Same buckets as Alpha Writer and the Grok pack. Chart bot uses the **Grok strings** on the sidecar (`primary_force`). Unclear → **`DARK`**. Never invent rates, wars, polls, or protocol stories to fill a tag.

| Docs | Role |
| --- | --- |
| [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md) | Alpha Writer NOTE tags (`force:credit` … `force:DARK`) |
| [grok/GROK-ALPHA-FIVE-FORCES.md](./grok/GROK-ALPHA-FIVE-FORCES.md) | Copy-paste pack; exact Chart bot enum |

There is no public dump of a private Grok five-force chat in this repo. World Monitor stays DARK unpaid.

## Learning loop

Not silent weight magic. After a thesis resolves, file a retro. Append PATTERN-EDGE-LOG. Do not retune pins in the dark.

**Viral PnL is never a training label.** Hype-thread dollar claims are a Chart-shot **reject** and are forbidden as fine-tune fuel.

## What Chart bot will not do

- Generate a “representative” candle when the tape is missing.
- Invent S/R, overlays, or macro.
- Place or suggest live orders.
- Treat MM journals or sniper screenshots as Chart shots.
- Call BOS alone `confluent`.
- Train on influencer / Discord / bot PnL.

Sleeves: **SOL / ETH** primary. **HYPE** DARK until a mocked adapter. Critique pins stay frozen (pivot N=2, VWAP UTC day, ATR pack defaults).
