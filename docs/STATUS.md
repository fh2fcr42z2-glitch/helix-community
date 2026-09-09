# Helix status for Grok (read this first)

**Auto-pull only sees `main`.** Use this file and other docs on **helix-community `main`**. Do not treat private `helix-cx` GitHub `main` as the live desk — that repo’s paper desk lives on open PR #1 until Call Me X merges it.

## What is true right now (2026-09-09)

| Piece | Truth |
|---|---|
| Public docs (this repo `main`) | LIVE — PoR/OFAC (+Binance sample), five-forces, data/memory, crew, research loop, Market Maker, quant/risk/fleet, TA / Chart shots / Chart bot / engine flow, wallet login, PnL honesty, Trench Narrative, **Reader**, **Grok prompt packs**, ta-learning contract (empty log) |
| Private `helix-cx` GitHub `main` | Hull / early stub — **not** the Fleet preview |
| Private `helix-cx` PR #1 | Paper desk + Fleet OS work in flight — merge only when Call Me X says |
| Execution | paper · `liveOrders` false · no unsupervised live orders |
| Fleet OS ridge | LIVE only for real metrics (print share, tape age, kills, FREE venues). **In Review / agent success stay DARK** — never invent a success % |
| Warehouse | stub + docs · tile DARK until enabled |
| PoR / OFAC | seed **counts only** · RPC join DARK |
| Five-force tags | default DARK until evidence assigns a force · Chart bot: `debt_cycle` / `internal_order` / `geopolitics` / `nature` / `inventiveness` / `DARK` |
| Risk gates | library present, flag off · never a live go-ahead by itself |
| World Monitor | DARK without a key |
| Market Maker | LIVE authorized (X 2026-09-09) · fee_income only · principal locked · venue DARK blocks · **SOL primary · ETH try-now · HYPE DARK until adapter** · Scout 2026-09-09: **Phoenix SOL CLOB PASS · ETH CEX+gas PASS · HYPE HL WARN** · CX wiring on PR #1 |
| Technical Analysis | TA critique **PASS**; first SOL/ETH Chart shot pack on desk (4 shots: SOL/ETH × 1h/4h) · all `setup_grade` **sketch** (TradingView guest = candles+volume only; SuperTrend/%B/RSI/VWAP **DARK**) · not `setup`/`confluent` · **HYPE** still DARK · CX Chart shots tab still wiring on helix-cx PR #1 · contract [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md) · files `helix-cowork/chart-shots/` (**may be unmounted**) |
| Chart bot | readable annotations + five-force spine · learning via ta-learning retros · CX tab on PR #1 · [CHART-BOT.md](./CHART-BOT.md) · log [`ta-learning/PATTERN-EDGE-LOG.md`](../ta-learning/PATTERN-EDGE-LOG.md) (empty — no fabricated edges) |
| Wallet login | wiring on helix-cx PR #1 · connect+DEX view · HYPE DARK · no key custody |
| PnL panel | wiring on helix-cx PR #1 · Coinbase+wallets · viral PnL DARK · no fabricated totals |
| Trench Narrative | wiring on helix-cx PR #1 · RSS free first · X API paid for scale · social heat ≠ size |
| Reader | doctrine + CX bay on PR #1 · five-force + myth filter · FREE ingest map · Alpha handoff rules · Grok republish **not before** 2026-09-14 |

## Rules that stop confusion
1. Unknown → **DARK / NULL**. Never invent metrics, whale labels, PnL, or balances.
2. Viral trading posts are **inspiration for process**, not Helix performance evidence.
3. Prepare ≠ execute. Live money needs **explicit human approval** — MM tickets were authorized by X on 2026-09-09 (journal `approval_ref`; `needs_human_approval=false` for that path).
4. If a PR is open and `main` is behind, say so once, then use **this STATUS** and community docs — don’t loop on “not merged” as if the desk doesn’t exist.
5. Launchpad nature (mass mint / skip-as-edge) ≠ MM fee-vault loop — [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md). Unverified bot PnL stays DARK.
6. TA critique pack lives on the desk box (`helix-cowork` briefs/notes — **may be unmounted**). Chart shots live under `helix-cowork/chart-shots/` (**may be unmounted** — do not invent PNGs or overlays). Public contract: [CHART-BOT.md](./CHART-BOT.md) + [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md) + [PATTERN-SETUPS.md](./PATTERN-SETUPS.md). Do not invent the pack file. Pins: pivot **N=2**, VWAP **UTC day**, ATR **pack defaults**, **BOS alone ≠ confluent**. Missing sidecar → DARK metadata. Guest candles+volume = **sketch**, never `setup`/`confluent`. Readable cards need **levels**, **invalidation**, **thesis_blurb**. Unclear macro → **DARK**. Learning is file-based (`ta-learning/` + PATTERN-EDGE-LOG), not silent weights. Viral PnL is never a training label.
7. **Reader** judges cited headlines only — ingest → five forces → myth filter → tape check → JSON, then Alpha Writer. **FREE ingest map** + **Alpha handoff rules** + **open ingest** (no archive.ph; paywalled body DARK) live on [READER.md](./READER.md) (Cowork fold; desk notes may be unmounted). **No fake headlines.** Tape and counts win vs psychology and vs `nieder_*` themes. Social heat ≠ size. Viral PnL DARK. CX bay on PR #1. **Grok republish not before 2026-09-14**; this STATUS on `main` is live now.

## Canonical docs on this `main`
- [CREW-HANDOFF.md](./CREW-HANDOFF.md) — one job per lane, veto/don’t-chase gates
- [ENGINE-FLOW.md](./ENGINE-FLOW.md) — anti-clog promotion (idea → cowork → Scout flag → CoS PR → warehouse/Fleet)
- [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md) — TA specialist, Chart shots; critique PASS; first pack **sketch**; readable cards; five-force spine; sidecar JSON; no invented levels; no orders
- [CHART-BOT.md](./CHART-BOT.md) — short public contract (readable shots, five-force spine, ta-learning loop, CX tab on PR #1)
- [PATTERN-SETUPS.md](./PATTERN-SETUPS.md) — `pattern_id` enum + setup_grade; invalidation required; hype PnL reject
- [`ta-learning/`](../ta-learning/) — file-based Chart bot retros + [PATTERN-EDGE-LOG](../ta-learning/PATTERN-EDGE-LOG.md) (empty; no fabricated edges)
- [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md)
- [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md)
- [POR-OFAC-SEEDS.md](./POR-OFAC-SEEDS.md)
- [RESEARCH-LOOP.md](./RESEARCH-LOOP.md) — research→code→backtest→live→post-mortem→fine-tune (Helix version)
- [MARKET-MAKER.md](./MARKET-MAKER.md) — LIVE-authorized fee-vault rotate loop (X 2026-09-09; principal locked)
- [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) — multi-sleeve desk map (SOL primary · ETH try-now · HYPE DARK until adapter) · Scout venue grades 2026-09-09 (no invented depth)
- [WALLET-LOGIN.md](./WALLET-LOGIN.md) — SIWS/SIWE connect; propose→popup; DEX panel real-or-DARK; no key custody
- [PNL.md](./PNL.md) — cross-source PnL (Coinbase + wallets + optional MM fee_income, labeled separate); incomplete badge; viral PnL DARK
- [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md) — launchpad nature vs MM (skip-as-edge; bot PnL DARK)
- [TRENCH-NARRATIVE.md](./TRENCH-NARRATIVE.md) — Trench hull = desk chrome; Narrative panel (posts/headlines); RSS free first; X API paid; social heat ≠ clip/size; no invented tweets
- [READER.md](./READER.md) — headline ingest → five forces → rhetoric/myth filter → tape check → READER JSON; FREE ingest map; Alpha handoff rules; optional `nieder_*` themes (no book excerpts); upstream of Alpha Writer; CX bay on PR #1; no fake headlines
- [QUANT-CONFIDENCE.md](./QUANT-CONFIDENCE.md) — R/Python/math confidence pack
- [RISK-GATES.md](./RISK-GATES.md) — walk-forward / DSR / Kelly (paper)
- [FLEET-OS.md](./FLEET-OS.md) — Ops Ridge REAL vs DARK
- [GROK-PROMPTS.md](./GROK-PROMPTS.md) — copy-paste Grok packs (`docs/grok/`)
- [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md)
