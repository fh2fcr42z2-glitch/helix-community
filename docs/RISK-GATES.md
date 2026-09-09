# Risk gates (walk-forward · DSR · Kelly) — public

Helix research/sizing gates. **Paper confidence tools — not unsupervised live authority.**  
Live money still needs Call Me X approval. See also [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md) and [RESEARCH-LOOP.md](./RESEARCH-LOOP.md).

---

# Cloud Agent brief — Risk gates: walk-forward, DSR, Kelly sizing (research scaffolding)

**Priority:** CoS sprint B (post helix-cx/pull/1)  
**Kind:** Statistical / sizing gates — research & risk-gate scaffolding only  
**Baseline:** [helix-cx/pull/1](https://github.com/fh2fcr42z2-glitch/helix-cx/pull/1) already has paper desk, kill strip, indicators, FREE marketdata adapters. **Do not duplicate adapters.**  
**Do not merge until review.** Helix is LIVE-CAPABLE but agents **never** place live orders. Gates are confidence tools; live execution still requires **explicit user go-ahead**.

## Suggested PR title

`feat(risk): walk-forward harness + DSR gate + Kelly fraction sizing cap (paper only)`

## Goal

Add a **research/risk-gate scaffolding** layer on helix-cx that:

1. Runs **walk-forward evaluation** over paper/backtest return series (no live order path).
2. Computes a **Deflated Sharpe Ratio (DSR)** gate (Bailey & López de Prado) and fails closed when the strategy does not clear a configured threshold.
3. Caps position size via **half-Kelly (or configurable Kelly fraction)** with explicit env-driven config.
4. Documents (and optionally stubs) **falsification** stretch: PBO and/or CPCV — mention in README + interface hooks; full implementation may be follow-on.

**Clear contract:** these gates increase confidence for paper research; they do **not** authorize live trading. Live remains behind explicit user go-ahead outside this PR.

## Target repo

- **helix-cx** — new modules under something like `src/lib/risk/` (or `src/lib/research/`), wired to existing paper desk / kill strip **as soft gates** (log + block paper size / flag UI), not as broker execution.

## Non-goals

- New marketdata adapters (Hyperliquid, F&G, Deribit, OKX, Bitget/Gate/HTX liqs, Binance/Bybit, etc. — already in PR #1).
- Broker keys, signed order paths, unsupervised live orders.
- Replacing the kill strip or paper desk — **compose with** them.
- Full production CPCV/PBO suite in v1 (stretch only).
- Inventing edge or claiming a strategy is “live-ready” because DSR passed.

## Proposed modules / tests

| Module (suggested) | Responsibility |
|--------------------|----------------|
| `src/lib/risk/walk-forward.ts` | Rolling / expanding train→test windows; emit per-fold metrics (Sharpe, returns, n trials). |
| `src/lib/risk/deflated-sharpe.ts` | DSR from observed SR, skew, kurtosis, number of trials `N`; gate `pass/fail` + reason. |
| `src/lib/risk/kelly.ts` | Kelly / half-Kelly fraction from win rate & payoff or from mean/variance of excess returns; apply **cap** `f = min(f_kelly * HELIX_KELLY_FRACTION, HELIX_KELLY_MAX)`. |
| `src/lib/risk/gates.ts` | Orchestrate WF → DSR → Kelly size recommendation; integrate with paper desk sizing (read-only recommendation or hard paper cap). |
| `src/lib/risk/falsification.ts` (stretch) | Interface + README notes for PBO / CPCV; stub returning `NOT_IMPLEMENTED` / DARK until filled. |
| Tests | Unit tests with **synthetic** return series (known SR); fixture folds; DSR monotonicity vs `N`; Kelly fraction clamps; no network, no broker mocks required. |

### Acceptance checks

1. **Walk-forward harness:** given a synthetic series + config (`HELIX_WF_TRAIN_BARS`, `HELIX_WF_TEST_BARS`, `HELIX_WF_STEP_BARS`), produces ≥1 fold with documented metrics; empty/short series → fail closed with explicit reason.
2. **DSR gate:** for a fixed SR, increasing trial count `N` **lowers** DSR (selection-bias correction); gate fails when DSR < `HELIX_DSR_MIN` (or p-value > threshold if implemented that way — document which).
3. **Kelly sizing:** with `HELIX_KELLY_FRACTION=0.5` (half-Kelly), recommended size ≤ half of full Kelly and ≤ `HELIX_KELLY_MAX`; never NaN/Inf; zero-edge → size 0.
4. **Paper-only:** no code path calls live order APIs; README states live still needs explicit user go-ahead; gates are confidence tools.
5. **No adapter duplication:** PR does not add/replace FREE marketdata adapters from PR #1.
6. **`npm test` green**; env **names only** in `.env.example` (placeholders, no secrets).
7. **Stretch (optional in same PR):** `falsification.ts` stub + short README section naming PBO / CPCV; or skip with “follow-on” note — do not block merge review on full CPCV.

## Config env var NAMES only

```
HELIX_WF_TRAIN_BARS=          # walk-forward train window length
HELIX_WF_TEST_BARS=           # walk-forward test window length
HELIX_WF_STEP_BARS=           # step / roll forward size
HELIX_WF_MIN_FOLDS=           # minimum folds required to evaluate
HELIX_DSR_MIN=                # minimum Deflated Sharpe to pass gate
HELIX_DSR_TRIALS_N=           # number of trials / strategies searched (selection bias)
HELIX_DSR_SR_BENCHMARK=       # optional SR null benchmark (often 0)
HELIX_KELLY_FRACTION=         # e.g. 0.5 for half-Kelly
HELIX_KELLY_MAX=              # hard cap on fraction of equity / notional
HELIX_KELLY_LOOKBACK_BARS=    # bars used to estimate edge for Kelly
HELIX_RISK_GATES_ENABLED=     # master switch for research gates (paper path)
HELIX_PBO_ENABLED=            # stretch: enable PBO path when implemented
HELIX_CPCV_N_GROUPS=          # stretch: CPCV group count when implemented
# No broker API keys. No live order toggles in this brief.
```

## References

- Bailey, D. H. & López de Prado, M. (2014). *The Deflated Sharpe Ratio: Correcting for Selection Bias, Backtest Overfitting, and Non-Normality.* Journal of Portfolio Management. SSRN: https://ssrn.com/abstract=2460551
- Bailey, D. H., Borwein, J. M., López de Prado, M. & Zhu, Q. J. (2014/2017). *The Probability of Backtest Overfitting.* Journal of Computational Finance. SSRN: https://ssrn.com/abstract=2326253
- López de Prado, M. (2018). *Advances in Financial Machine Learning* — Combinatorial Purged Cross-Validation (CPCV).
- Thorp, E. O. — Kelly criterion / half-Kelly practice (position sizing literature).
- Existing helix-cx surfaces to compose with (do not replace): paper desk, kill strip, indicators — see PR #1.



## Related — do not duplicate SQL pack

Canonical **Grok SQL / dataset prompts** (schema, ETL, DQ, walk-forward splits, DSR tables, DARK charter):

- `/workspace/helix-prompts/GROK-SQL-DATASET-PACK.md` (**ship-to-X copy**)
- `/workspace/helix-cowork/prompts/grok-sql-dataset-pack.md` (Cowork mirror; prefer helix-prompts when they diverge)

Memory layers: `/workspace/helix-cowork/notes/memory-flexibility.md`

**This brief owns:** TypeScript risk-gate modules + UI/kill-strip composition + env `HELIX_KELLY_FRACTION` / DSR thresholds.  
**SQL pack owns:** `wf_split` / `fact_metric_run` / DSR result DDL, warehouse quality_flag, ETL.  
Cloud Agent implementing gates should **import table shapes from the SQL pack** (or warehouse stub) rather than inventing a second schema here.

## Out of scope

- Broker API keys, secrets, or signed trading endpoints  
- Unsupervised / agent-initiated **live** orders (agents never place live orders)  
- Duplicate FREE marketdata adapters already in helix-cx/pull/1  
- Claiming live readiness from passing DSR alone  
- Merging without human review  

## Index note (parent)

Parent may update `briefs/README.md` if needed — list this brief under **CoS sprint B**.
