# Chart bot learning (`ta-learning/`)

File-based retros for the Chart bot. **Not** silent model-weight updates. **Not** a PnL scoreboard.

Public contract: [docs/CHART-BOT.md](../docs/CHART-BOT.md) · [docs/TECHNICAL-ANALYSIS.md](../docs/TECHNICAL-ANALYSIS.md).

Paper-only. No secrets. No fake charts. No fabricated macro.

Desk copies may also live under `helix-cowork/ta-learning/` (**may be unmounted**). If that dir is missing, do not invent retros. This folder is the **public schema + empty log**.

## What belongs here

| File | Job |
| --- | --- |
| [PATTERN-EDGE-LOG.md](./PATTERN-EDGE-LOG.md) | Running log of pattern observations (one row per resolved claim) |
| [RETRO.template.md](./RETRO.template.md) | Copy to `YYYY-MM-DD-<slug>.md` when a thesis resolves |
| Dated retros (`YYYY-MM-DD-*.md`) | What was claimed vs what printed; invalidation; force tag; DARK list |

## Rules

1. **Handoffs via files.** A chat takeaway is not a retro.
2. **Viral PnL is never a training label.** Influencer screenshots, Discord call-outs, unverified bot PnL do not enter the log as evidence that a `pattern_id` works.
3. **Unclear force → `DARK`.** Do not invent macro in the retro to look complete.
4. **Pins stay frozen** until a later TA critique PASS (pivot N=2, VWAP UTC day, ATR pack defaults, BOS alone ≠ confluent).
5. Negative results are first-class. A miss is a completed row, not a deleted file.

This is stage 6 (fine-tune) for TA: [docs/RESEARCH-LOOP.md](../docs/RESEARCH-LOOP.md). Walk-forward / DSR / Kelly stay paper: [docs/RISK-GATES.md](../docs/RISK-GATES.md).
