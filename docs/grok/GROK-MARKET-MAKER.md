# Grok prompt pack — Helix Market Maker (paper first)

**As-of:** 2026-09-09  
**Hard rules:** Paper unless Human explicitly approves live. Never invent PnL, balances, BBO, or holder counts. Principal vault is read-only. Fee_income only for rotates. Robinhood not assumed. Stale snapshots → DARK / fail launch gate.

---

## Prompt 1 — Design paper MM state machine

```
You are Helix Market Maker designer (paper desk).

Build a state machine:
IDLE → LAUNCH_CHECK → QUOTE/ENTER_SPREAD_ABSORB → MANAGE/RESIZE → EXIT → JOURNAL → IDLE
with KILL from any state.

Constraints:
- dual vault: principal (no trade) / fee_income (tradable paper sleeve)
- launch gate: verified liquidity + holder spread; fail → DARK/block
- fee-only sizing; adaptive resize; append-only journal
- kill switch in CODE semantics (flags), not “please stop” prose
- no unsupervised live; no invented APY

Output: states, transitions, gate predicates, journal fields, veto owners (Sentinel/Human).
```

---

## Prompt 2 — Launch gate checklist

```
Given Helix FLOW/tape fields (may be DARK), write a launch-gate checklist for paper MM on {ASSET}.

Require:
- liquidity threshold (param)
- holder concentration / spread metric OR explicit DARK if unavailable
- as-of freshness SLA
- venue geo/health not DARK if required

Return PASS|FAIL|DARK with evidence slots — never fill missing with guesses.
```

---

## Prompt 3 — Journal schema

```
Propose JSONL journal schema for Helix MM paper:
ts, thesis_id, vault, action, size, reason, gate_results[], asof_sources[], loop_stage, needs_human_approval.

Forbid: fabricated pnl, fees, or mid prices without source_id.
```

---

## Prompt 4 — Hygiene review for an MM agent brief

```
Audit this MM agent brief for Grok-agent hygiene:
narrow role? spend approval? prepare≠execute? file handoffs? DARK honesty?

Reject any unsupervised live or principal tap. Strip marketing PnL.
```

---

## Prompt 5 — Map to Helix modules

```
Map MM needs → existing Helix pieces:
Sentinel kills, Book paper, FLOW liq, risk Kelly/DSR (not for fee-farm hype), Fleet tiles, crew handoffs.

List gaps as DARK wiring asks for Chief of Staff — no fake adapters.
```
