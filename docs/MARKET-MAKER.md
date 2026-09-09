# Helix Market Maker (LIVE — X authorized)

Inspiration: fee-farm rotate process. PnL stories stay DARK — not Helix evidence.

**Mode: LIVE** — Call Me X authorized all MM tickets live on 2026-09-09 (no paper default).  
`approval_ref`: `mm-chat:t1u+t4u 2026-09-09 America/Chicago — X: live all tickets no paper + Push to the GitHub`

## Keep
1. Dual vaults: `principal` read-only · `fee_income` only tradable stake
2. LaunchGate: liquidity + holder spread (missing/stale → DARK → block)
3. Trade fee_income only; never debit principal
4. Enter only if spread absorbable
5. `size_basis=both` (last_close + depth_cap)
6. Kill OFF → may rotate; kill ON → code stops new entries
7. fee_income 0 or fee source DARK → SKIP (never stub fees)
8. Venue DARK → block (never stub fills)

## Gate checklist v1
| Check | Rule |
|---|---|
| Kill | PASS only if OFF; else FAIL |
| Liquidity | ≥ min + fresh as-of; else FAIL (stale=FAIL) |
| Holders | present + fresh → PASS; missing/stale → DARK → block |
| Venue/geo | if required: missing → DARK → block |
| Vault | fee_income only; principal rejected |
| Live | authorized 2026-09-09 — journal approval_ref; needs_human_approval=false for this path |
| Fees | fee_income > 0 with source_id else SKIP |

## Journal JSONL (append-only)
ts, thesis_id, vault, action, size, reason, gate_results[{check,status,evidence,asof,source_id}], asof_sources[], loop_stage (IDLE|LAUNCH_CHECK|ENTER|MANAGE|EXIT|JOURNAL), needs_human_approval, approval_ref, kill_switch, fee_income_balance_asof (+source_id), last_close_size, spread_budget, size_basis (=both).  
Forbid pnl/fees/mids without source_id.

## Vocabulary
Helix labels only (Sentinel / Sizing / Ops). No city/heist UI names.

## Multi-sleeve (SOL / ETH / HYPE)

Desk map: [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md). **SOL** primary (lower fees) · **ETH** try-now (wider spread + gas budget) · **HYPE** DARK until adapter. Discovery/sniper six lanes stay on a **separate journal** — do not mix with MM.

## Out of scope
Viral PnL as evidence; trading principal; stub fills when venue/liq/holders/fees are DARK; quoting HYPE before a mocked adapter; collapsing sleeves into one ledger.

Launchpad **nature** (mass mint, rare graduation, skip-as-edge) is not this fee-vault loop. Curve-snipe ≠ LaunchGate. See [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md).
