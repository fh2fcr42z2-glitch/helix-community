# Grok prompt pack — Helix crew handoff discipline

**As-of:** 2026-09-09 (America/Chicago)  
**Source inspiration:** Process discipline patterns seen in public “crew/ops” trading threads (e.g. GPTHEIST-style role splits).  
**Explicitly DARK / out of scope:** Any PnL, win-rate, or “immortal” performance claims from those posts — **unverified**. Steal **workflow**, not mythology.

**Helix mapping (no themed UI codenames in product):** use role labels Scout · Cowork · CoS · Tape/CX · FLOW · Sentinel · Alpha Writer · Quant · Human (X).

---

## Five hard rules

1. **One owner** per job — no overlapping mandates.  
2. **File/evidence handoffs** — next agent receives paths + as-of, not vibes.  
3. **Evidence + as-of or DARK** — missing data stays DARK; never invent.  
4. **Prepare ≠ execute** — research/sizing/briefs ≠ live orders. Money needs **human approval**.  
5. **Veto = criterion + owner** — name who can block and on what measurable rule.

---

## Role → Helix gate (discipline only)

| Discipline cue (internal) | Helix owner | Gate / handoff |
|---------------------------|-------------|----------------|
| Volume before price | **Tape / CX** (+ Scout data) | Prefer volume/OI/participation evidence before price narrative |
| Block if no exit liquidity | **Sentinel** | Kill / reject when verified DEX/pool exit liquidity below threshold (existing `$100k` kill pattern) |
| Exact reset conditions | **Sentinel + Risk** | Prewrite invalidate/reset rules before size; log in blotter/reason |
| Pullback + invalidation, never chase | **Tape / paper Book** | Entry rules require pullback + invalidation level; chase → reject |
| Social vs on-chain volume; filter paid noise | **Alpha Writer** (+ FLOW) | X/TG claims need on-desk volume/FLOW corroboration or DARK |
| Reject stale holder/liquidity snapshots | **FLOW / Scout** | Snapshot age > SLA → DARK; LISBON-style freshness |
| Size to pool depth / exit | **Sentinel / sizing** | Cap size to exit liquidity / Half-Kelly after gates |
| One compressed brief | **Cowork → CoS** | Single handoff brief per dig (path + delta + ask) |
| Position / exit / change log | **Book + ProcessLog** | Append-only reasons; no silent edits to exits |
| One final report; human $ approval | **CoS → Human (X)** | PROFESSOR-style: CoS consolidates; X approves money |

---

## Prompt — compress a dig into a crew handoff

```
You are Helix Cowork/CoS handoff writer. Produce ONE compressed brief.

Rules: one owner; evidence+as-of or DARK; prepare≠execute; no invented PnL; no themed heist codenames in user-facing copy.

Input:
JOB: {one job}
OWNER: {Helix role}
EVIDENCE_PATHS: {files/URLs}
AS_OF: {timestamp + zone}
ASK_FOR_NEXT: {what CoS/Cloud Agent/X must do}

Output:
- owner
- gate_checks[] (criterion, pass|fail|DARK, evidence ref)
- veto (criterion, owner) or none
- artifact_paths[]
- next_owner
- money_action: none | needs_human_approval
```

---

## Prompt — audit a desk decision for handoff gaps

```
Audit this Helix decision for crew-handoff discipline.

Check five rules: one owner; file handoffs; evidence+as-of or DARK; prepare≠execute; veto named.

Flag any chase entry, stale liquidity, social-only alpha, or size>exit depth.

Return PASS|REVISE|REJECT with bullets. Ignore any third-party PnL claims as DARK.
```

---

## Prompt — map gates → Fleet Ops Ridge metrics

```
Propose Ops Ridge / Fleet OS cards that reflect handoff gates with REAL metrics only:
- tape freshness / volume-before-price proxy
- exit-liquidity kill count
- reject reasons: chase, stale snapshot, social-only
- briefs awaiting CoS
- money actions pending human approval (count of flags — not dollars invented)

If metric can’t be sourced from Helix APIs/files → card status DARK.
No fake autonomy %. No themed city UI labels.
```

*Canonical for Grok main: helix-community `docs/CREW-HANDOFF.md` when CoS publishes.*
