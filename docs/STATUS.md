# Helix status for Grok (read this first)

**Auto-pull only sees `main`.** Use this file and other docs on **helix-community `main`**. Do not treat private `helix-cx` GitHub `main` as the live desk — that repo’s paper desk lives on open PR #1 until Call Me X merges it.

## What is true right now (2026-09-09)

| Piece | Truth |
|---|---|
| Public docs (this repo `main`) | LIVE — PoR/OFAC (+Binance sample), five-forces, data/memory, crew, research loop, Market Maker, quant/risk/fleet, **Grok prompt packs** |
| Private `helix-cx` GitHub `main` | Hull / early stub — **not** the Fleet preview |
| Private `helix-cx` PR #1 | Paper desk + Fleet OS work in flight — merge only when Call Me X says |
| Execution | paper · `liveOrders` false · no unsupervised live orders |
| Fleet OS ridge | LIVE only for real metrics (print share, tape age, kills, FREE venues). **In Review / agent success stay DARK** — never invent a success % |
| Warehouse | stub + docs · tile DARK until enabled |
| PoR / OFAC | seed **counts only** · RPC join DARK |
| Five-force tags | default DARK until evidence assigns a force |
| Risk gates | library present, flag off · never a live go-ahead by itself |
| World Monitor | DARK without a key |
| Market Maker | LIVE authorized (X 2026-09-09) · fee_income only · principal locked · venue DARK blocks · **SOL primary · ETH try-now · HYPE DARK until adapter** · CX wiring on PR #1 |

## Rules that stop confusion
1. Unknown → **DARK / NULL**. Never invent metrics, whale labels, or PnL.
2. Viral trading posts are **inspiration for process**, not Helix performance evidence.
3. Prepare ≠ execute. Live money needs **explicit human approval** — MM tickets were authorized by X on 2026-09-09 (journal `approval_ref`; `needs_human_approval=false` for that path).
4. If a PR is open and `main` is behind, say so once, then use **this STATUS** and community docs — don’t loop on “not merged” as if the desk doesn’t exist.

## Canonical docs on this `main`
- [CREW-HANDOFF.md](./CREW-HANDOFF.md) — one job per lane, veto/don’t-chase gates
- [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md)
- [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md)
- [POR-OFAC-SEEDS.md](./POR-OFAC-SEEDS.md)
- [RESEARCH-LOOP.md](./RESEARCH-LOOP.md) — research→code→backtest→live→post-mortem→fine-tune (Helix version)
- [MARKET-MAKER.md](./MARKET-MAKER.md) — LIVE-authorized fee-vault rotate loop (X 2026-09-09; principal locked)
- [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) — multi-sleeve desk map (SOL primary · ETH try-now · HYPE DARK until adapter)
- [QUANT-CONFIDENCE.md](./QUANT-CONFIDENCE.md) — R/Python/math confidence pack
- [RISK-GATES.md](./RISK-GATES.md) — walk-forward / DSR / Kelly (paper)
- [FLEET-OS.md](./FLEET-OS.md) — Ops Ridge REAL vs DARK
- [GROK-PROMPTS.md](./GROK-PROMPTS.md) — copy-paste Grok packs (`docs/grok/`)
- [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md)
