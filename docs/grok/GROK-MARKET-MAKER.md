# Grok prompt pack — Helix Market Maker (LIVE — X authorized)

**As-of:** 2026-09-09  
**Mode: LIVE** — Call Me X authorized all MM tickets live on 2026-09-09 (no paper default).  
`approval_ref`: `mm-chat:t1u+t4u 2026-09-09 America/Chicago — X: live all tickets no paper + Push to the GitHub`

**Hard rules:** Dual vaults (`principal` read-only · `fee_income` only tradable stake). LaunchGate: liquidity + holder spread (missing/stale → DARK → block). Trade `fee_income` only; never debit principal. Enter only if spread absorbable. `size_basis=both` (last_close + depth_cap). Kill OFF → may rotate; kill ON → code stops new entries. `fee_income` 0 or fee source DARK → SKIP (never stub fees). Venue DARK → block (never stub fills). Never invent PnL, balances, BBO, or holder counts. Helix labels only (Sentinel / Sizing / Ops). Journal `approval_ref`; `needs_human_approval=false` for this authorized path. CX wiring lives on helix-cx PR #1.

Canonical process: [MARKET-MAKER.md](../MARKET-MAKER.md) · desk truth: [STATUS.md](../STATUS.md)

---

## Prompt 1 — Design LIVE MM state machine

```
You are Helix Market Maker designer (LIVE — X authorized 2026-09-09; no paper default).

Build a state machine:
IDLE → LAUNCH_CHECK → ENTER → MANAGE → EXIT → JOURNAL → IDLE
with KILL from any state.

Constraints:
- dual vault: principal (read-only, never debit) / fee_income (only tradable LIVE stake)
- launch gate: verified liquidity + holder spread; missing/stale → DARK → block
- trade fee_income only; size_basis=both (last_close + depth_cap)
- enter only if spread absorbable
- kill OFF → may rotate; kill ON → code stops new entries
- fee_income 0 or fee source DARK → SKIP (never stub fees)
- venue DARK → block (never stub fills)
- kill switch in CODE semantics (flags), not “please stop” prose
- journal approval_ref = mm-chat:t1u+t4u 2026-09-09 America/Chicago — X: live all tickets no paper + Push to the GitHub
- needs_human_approval=false for this authorized path
- no invented APY / PnL

Output: states, transitions, gate predicates, journal fields, veto owners (Sentinel / Sizing / Ops).
```

---

## Prompt 2 — Launch gate checklist

```
Given Helix FLOW/tape fields (may be DARK), write a launch-gate checklist for LIVE MM on {ASSET}.

Mode is LIVE (X authorized 2026-09-09). Do not default to paper.

Require:
- Kill: PASS only if OFF; else FAIL
- Liquidity: ≥ min + fresh as-of; else FAIL (stale=FAIL)
- Holders: present + fresh → PASS; missing/stale → DARK → block
- Venue/geo: if required, missing → DARK → block (never stub fills)
- Vault: fee_income only; principal rejected
- Live: authorized — journal approval_ref; needs_human_approval=false for this path
- Fees: fee_income > 0 with source_id else SKIP (never stub fees)

Return PASS|FAIL|DARK with evidence slots — never fill missing with guesses.
```

---

## Prompt 3 — Journal schema

```
Propose JSONL journal schema for Helix MM LIVE (append-only):
ts, thesis_id, vault, action, size, reason,
gate_results[{check,status,evidence,asof,source_id}],
asof_sources[], loop_stage (IDLE|LAUNCH_CHECK|ENTER|MANAGE|EXIT|JOURNAL),
needs_human_approval, approval_ref, kill_switch,
fee_income_balance_asof (+source_id), last_close_size, spread_budget,
size_basis (=both).

approval_ref must be:
mm-chat:t1u+t4u 2026-09-09 America/Chicago — X: live all tickets no paper + Push to the GitHub

needs_human_approval=false for this authorized path.

Forbid: pnl, fees, or mids without source_id. Never invent balances or fills.
```

---

## Prompt 4 — Hygiene review for an MM agent brief

```
Audit this MM agent brief for Grok-agent hygiene:
narrow role? dual vault (principal locked / fee_income only)? fail-closed DARK?
kill in CODE? journal approval_ref? Helix labels only (Sentinel / Sizing / Ops)?

Reject: paper-first default (LIVE is authorized 2026-09-09), principal tap,
stub fills when venue/liq/holders/fees are DARK, viral PnL as evidence,
city/heist UI names.

Keep hard rails. Strip marketing PnL.
```

---

## Prompt 5 — Map to Helix modules

```
Map LIVE MM needs → existing Helix pieces:
Sentinel kills, fee_income vault, FLOW liq + holders, risk Kelly/DSR (not for fee-farm hype), Fleet tiles, crew handoffs (Sentinel / Sizing / Ops).
CX wiring is on helix-cx PR #1 — list that as wiring, not as a missing go-ahead.

List gaps as DARK wiring asks for Chief of Staff — no fake adapters, no stub fills.
```
