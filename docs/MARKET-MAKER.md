# Helix Market Maker (fork — process only)

Inspiration: public fee-farm / rotate loops (e.g. @0xboan Robinhood token-launch story) + Grok Bot ops hygiene (@bober_smart).  
**Use the loop. PnL stories ($100 → $2,300, iPhone bets) stay DARK — not Helix evidence.**

## Mode
**LIVE** — Call Me X authorized all MM tickets **2026-09-09**. No paper default. Journal `approval_ref`.

## What we fork (keep)
1. **Two vaults:** `principal` (read-only, never trade) vs `fee_income` (only tradable **LIVE** stake).
2. **Launch gate:** check liquidity + holder spread before a launch/listing is worth pushing.
3. **Fee cut:** earn from flow against the market (maker rebate / simulated launch fee) — win or lose for the other side.
4. **Trade only fee income** already collected — never touch starting principal directly.
5. **Entry only when setup absorbs spread cleanly** (exit liquidity / spread budget passes).
6. **Resize** — canonical rule below (`size_basis = both`). Never a flat fixed bet.
7. **Rotate on a schedule** once the cycle is proven by hand once.

## What we change (Helix — no confusion)
| Viral claim | Helix Market Maker |
|---|---|
| Robinhood token launches | Abstract **venue adapter**. Real launch/rebate only when a FREE/verified venue exists — else DARK (no stub fills) |
| No confirmation / no babysitting | **LIVE may auto-rotate while `HELIX_KILL_SWITCH` / MM kill is OFF. When kill is ON, code stops new entries.** Kill does **not** enable rotation. |
| Unverified $ targets | No target PnL in prompts; success = gates fired correctly + journals |
| Unsupervised by default | LIVE is authorized (X 2026-09-09); still fail-closed on DARK/FAIL gates; journal `approval_ref` |

## Resize (canonical — one rule)
**`size_basis = both`:** primary size from `last_close_size` / last cycle outcome; hard clamp by exit-depth / FeeVault / max risk (`depth_cap`). Never flat fixed bet. Never debit principal.

## Fee income
**If `fee_income` balance is 0 or fee source is DARK → journal `SKIP` and do not enter. Never stub fake fees.**

## Launch gate (holders)
**Missing holder spread/concentration or stale as-of → status DARK → block entry (fail-closed). Do not invent holders.** Liquidity stale → **FAIL**. Venue missing → **DARK → block**. Never invent data/PnL.

## Cycle (every run)
```
LaunchGate(liquidity, holder_spread)
  → FAIL or DARK: skip / block
  → CollectFeeIncome (ledger or venue rebate; SKIP if 0 or DARK)
  → SizeFromLastClose (`size_basis = both`, fee_vault only)
  → EntryIfSpreadAbsorbable
  → Exit / rotate (LIVE while kill is OFF; kill does not enable rotation)
  → Journal (Ops log + approval_ref)
```

## Hard rules
- Principal vault balance is **read-only** for trading paths. Never trade principal.
- `fee_income` is the only tradable **LIVE** stake.
- **LIVE may auto-rotate while `HELIX_KILL_SWITCH` / MM kill is OFF. When kill is ON, code stops new entries.** Kill does **not** enable rotation.
- Unknown liquidity / holders / fees / venue → **DARK**, do not invent. Never stub fills when DARK.
- Fits research loop: LaunchGate∈Research, journal∈Post-mortem, resize∈Fine-tune.
- Fits crew handoff: **Sentinel** (liquidity veto); **Sizing** (size-to-exit); **Ops log** (journal).

## Gate checklist (v1)
Each row is **PASS**, **FAIL**, or **DARK**. FAIL and DARK both **block entry**.

| Check | Rule |
|---|---|
| Kill | PASS only if `HELIX_KILL_SWITCH` / MM kill is **OFF**; else **FAIL**. Kill OFF is required to rotate; kill does **not** enable rotation. |
| Verified liquidity | PASS if ≥ min **and** as-of is fresh; else **FAIL** (stale = FAIL) |
| Holder spread / concentration | present **and** fresh → PASS; missing or stale as-of → **DARK → block** |
| Venue / geo | required: present → PASS; missing → **DARK → block** (no stub fills) |
| Vault | `fee_income` only; balance > 0 with sourced fees. Balance 0 or fee source DARK → journal `SKIP` (do not enter). Never debit principal. |
| Live | **LIVE authorized** (Call Me X 2026-09-09); journal `approval_ref`; venue still required (DARK → block, no stub fills) |

## Journal JSONL (append-only)
One object per line. **No invented PnL.** Do not write `pnl`, `fees`, or `mids` without a `source_id`.

Required fields:

- `ts`
- `thesis_id`
- `vault` (`principal` \| `fee_income`)
- `action`
- `size`
- `reason`
- `gate_results` — array of `{check, status, evidence, asof, source_id}`
- `asof_sources[]`
- `loop_stage` (`IDLE` \| `LAUNCH_CHECK` \| `ENTER` \| `MANAGE` \| `EXIT` \| `JOURNAL`)
- `needs_human_approval`
- `kill_switch`
- `fee_income_balance_asof` (+ `source_id`)
- `last_close_size`
- `spread_budget`
- `size_basis` (`both`)
- `approval_ref`

Forbidden without `source_id`: `pnl`, `fees`, `mids`.

## Bot hygiene (keep)
- Narrow role: Market Maker owns this loop only.
- Secrets via takeover / secret-request — never chat paste.
- Journal `approval_ref` on every LIVE cycle; shared box is **not** a security boundary between bots.

## Out of scope
- Citing viral PnL as backtest or live result
- Trading principal
- Importing Robinhood as a required dependency without a real adapter
- Stubbing fills when DARK
