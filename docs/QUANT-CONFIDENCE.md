# Quant confidence pack (public)

**Paper / live-capable research.** Curated R + Python + math pointers for Helix risk gates.  
**Not financial advice. No secrets. Unknown → DARK.**  
Full Cowork working copy may be richer; this is the Grok-readable `main` edition (2026-09-09).

---

# Helix LIVE-CAPABLE confidence pack

**Date:** 2026-09-09 (America/Chicago)  
**Scope:** Paper research / resource curation only — **no trading, no secrets, no live wiring.**  
**Rule:** Verified links preferred. `DARK` = 404/unreachable at fetch time; `UNKNOWN` = not verified or unsure how Helix should consume it; `PAYWALL` = DOI/SSRN/publisher gate for full text (abstract/metadata still useful).

---

## 1. R / stats

| Package / topic | URL | Why Helix cares | Cost |
|-----------------|-----|-----------------|------|
| **PerformanceAnalytics** | https://CRAN.R-project.org/package=PerformanceAnalytics · refman: https://cran.r-project.org/web/packages/PerformanceAnalytics/refman/PerformanceAnalytics.html · GitHub: https://github.com/braverock/PerformanceAnalytics | Canonical Sharpe/Sortino/drawdown/VaR/ES and non-normal return analytics for tearsheets and live risk gates. | FREE (GPL) |
| **quantmod** | https://CRAN.R-project.org/package=quantmod · https://www.quantmod.com/ · https://github.com/joshuaulrich/quantmod | Data ingest + charting + model wrappers; rapid research scaffolding around OHLC/returns. | FREE (GPL-3) |
| **rugarch** | https://CRAN.R-project.org/package=rugarch · refman: https://cran.r-project.org/web/packages/rugarch/refman/rugarch.html | Univariate GARCH/ARFIMA for vol forecasts, rolling density backtests, risk measures under fat tails. | FREE |
| **xts** | https://CRAN.R-project.org/package=xts | Time-indexed matrix standard for finance pipelines; interoperability layer for PA/quantmod/rugarch. | FREE |
| **zoo** | https://CRAN.R-project.org/package=zoo | Irregular/regular series base that xts extends; needed for alignment, NA, and merge hygiene. | FREE |
| **quantstrat `walk.forward`** | https://rdrr.io/github/braverock/quantstrat/man/walk.forward.html · repo: https://github.com/braverock/quantstrat | Rolling / anchored walk-forward param selection — causal OOS protocol template for Helix reports. | FREE (GitHub; **not** primary CRAN package index — treat install as UNKNOWN until pinned) |
| **PortfolioTesteR walk-forward** | https://rdrr.io/cran/PortfolioTesteR/src/R/walk_forward.R · https://CRAN.R-project.org/package=PortfolioTesteR | CRAN-side rolling IS/OOS optimization + OOS stitch pattern. | FREE |
| **caret / caretForecast** | caret: https://CRAN.R-project.org/package=caret · caretForecast: https://CRAN.R-project.org/package=caretForecast · README: https://cran.r-project.org/web/packages/caretForecast/readme/README.html | ML-for-finance training discipline: train-only transforms, conformal intervals, horizon-aware validation. | FREE |
| **Causal / leakage pointers (R + general)** | Walk-forward leakage note (public essay): https://itstedpark.medium.com/walk-forward-validation-for-financial-ml-avoiding-leakage-in-time-series-experiments-8b98b2100f01 · Purged CV concept writeup: https://www.luxalgo.com/library/concept/purged-cross-validation/ | Helix must forbid random CV, fit-on-full-sample scaling, and label overlap; purge/embargo before any ML signal. | FREE (secondary blogs — prefer AFML/CPCV papers in §3 for doctrine) |

---

## 2. Python quant

| Library | Official docs / GitHub | Why Helix cares | Cost |
|---------|------------------------|-----------------|------|
| **vectorbt** | Docs: https://vectorbt.dev/ · GitHub: https://github.com/polakowo/vectorbt/ | Vectorized multi-param backtests + walk-forward tooling; fast research sweeps (OSS). PRO is separate product. | OSS FREE; **vectorbt PRO** = paid (https://vectorbt.pro/) |
| **backtesting.py** | https://kernc.github.io/backtesting.py/ · API: https://kernc.github.io/backtesting.py/doc/backtesting/backtesting.html · GitHub: https://github.com/kernc/backtesting.py | Lightweight bar-loop strategy API; good for readable unit-style strategy tests. | FREE |
| **zipline-reloaded** | Docs: https://zipline.ml4trading.io/ · GitHub: https://github.com/stefan-jansen/zipline-reloaded | Event-driven Quantopian-lineage engine kept alive for research / book pipelines. | FREE |
| **Lean / QuantConnect** | GitHub: https://github.com/QuantConnect/Lean · Cloud platform: https://www.quantconnect.com/ | Institutional-style engine patterns (portfolio construction, brokerage models, live/paper parity). Cloud tiers beyond OSS Lean = paid/UNKNOWN for Helix hosting. | Lean OSS FREE; QC cloud = freemium/paid |
| **Riskfolio-Lib** | Docs: https://riskfolio-lib.readthedocs.io/en/latest/ · GitHub: https://github.com/dcajasn/Riskfolio-Lib | CVXPY portfolio opt (CVaR, risk parity, HRP, constraints) for sizing / risk budgets. | FREE (OSS); author book/course = paid optional |
| **PyPortfolioOpt** | Docs: https://pyportfolioopt.readthedocs.io/en/latest/ · GitHub: https://github.com/robertmartin8/PyPortfolioOpt | Efficient frontier, Black–Litterman, shrinkage, HRP — classical sizing baselines. | FREE |
| **arch** (GARCH) | Docs: https://arch.readthedocs.io/en/latest/ · GitHub: https://github.com/bashtage/arch | Python GARCH/vol, bootstrap, multiple-comparison hooks for risk/vol targeting. | FREE |
| **hmmlearn** | Docs: https://hmmlearn.readthedocs.io/ · GitHub: https://github.com/hmmlearn/hmmlearn | Gaussian HMM regimes for risk-on/off gates (pair with vectorbt signals in research only). | FREE |
| **scikit-learn** | https://scikit-learn.org/stable/ · GitHub: https://github.com/scikit-learn/scikit-learn | Feature pipelines / models — **only** with purged/walk-forward CV; never iid `KFold` on returns. | FREE |

---

## 3. Math / algos / falsification

| Topic | Primary citation / link | Status | Why Helix cares |
|-------|-------------------------|--------|-----------------|
| **Kelly / Half-Kelly** | Thorp, E. O. — “The Kelly Criterion in Blackjack, Sports Betting, and the Stock Market” (PDF commonly hosted): https://gwern.net/doc/statistics/decision/2006-thorp.pdf · Survey: MacLean, Thorp, Ziemba — *The Kelly Capital Growth Investment Criterion* (World Scientific) DOI book: https://doi.org/10.1142/7598 · Fractional Kelly properties: https://doi.org/10.1080/14697688.2010.506108 · Overview: https://en.wikipedia.org/wiki/Kelly_criterion | PDF host = tertiary; DOI book/paper = PAYWALL possible | Full Kelly maximizes growth but path-risk is brutal; **Half-Kelly (or ≤½)** is the practical cap when edge is estimated with error. |
| **Deflated Sharpe Ratio (DSR)** | Bailey & López de Prado (2014), *JPM* 40(5):94–107 — DOI: https://doi.org/10.3905/jpm.2014.40.5.094 · SSRN: https://doi.org/10.2139/ssrn.2460551 (also cited as SSRN 2308657 in secondary sources — prefer DOI) | PAYWALL (JPM); SSRN often FREE preprint | Corrects Sharpe for **multiple testing + non-normality**; Helix live-size gate should require DSR / PSR-style significance after counting trials *N*. |
| **Probability of Backtest Overfitting (PBO)** | Bailey, Borwein, López de Prado, Zhu — *Journal of Computational Finance* — SSRN: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2326253 · Author PDF: https://davidhbailey.com/dhbpapers/backtest-prob.pdf · Risk.net TOC: https://www.risk.net/journal-of-computational-finance/2471206/the-probability-of-backtest-overfitting · DOI family often cited: https://doi.org/10.21314/JCF.2016.322 | Author PDF = FREE (verified fetch 200); journal = PAYWALL | CSCV → PBO; reject strategies when IS winner systematically loses to OOS median. |
| **CPCV (Combinatorial Purged CV)** | López de Prado, *Advances in Financial Machine Learning* (Wiley, 2018) — Chapters on CV / backtesting through CV · Practitioner digest: https://ml4trading.io/docs/diagnostic/methods/cpcv/ | Book = paid; digest = FREE secondary | Many purged/embargoed paths → distribution of OOS outcomes + input matrix for PBO; superior to single walk-forward path alone. |
| **Pseudo-mathematics / overfitting essay** | Bailey et al., *Notices of the AMS* (2014): https://www.ams.org/notices/201405/rnoti-p458.pdf | FREE PDF | Readable doctrine: inflated IS Sharpe from parameter search is expected under noise. |
| **HMM regimes** | Hamilton, J. D. (1989), “A New Approach to the Economic Analysis of Nonstationary Time Series and the Business Cycle,” *Econometrica* — JSTOR/DOI commonly: https://doi.org/10.2307/1912559 | PAYWALL | Classical Markov-switching regimes; Helix can use regime probs as risk multipliers, not as free alpha. |
| **Copulas (high level)** | Patton (2004+) time-varying / switching-copula literature; survey entry: “Hidden Markov Structures for Dynamic Copulae” DOI: https://doi.org/10.1017/s0266466614000607 · Crypto HMM-copula example arXiv: https://ar5iv.labs.arxiv.org/html/2307.06400 | Mixed FREE/PAYWALL | Tail dependence ≠ linear corr; stress co-crash risk before sizing multi-leg books. Implementation depth = UNKNOWN for Helix v1. |
| **Microstructure / execution** | Almgren & Chriss (2000/2001), “Optimal Execution of Portfolio Transactions,” *Journal of Risk* — DOI: https://doi.org/10.21314/JOR.2001.041 · Wikipedia summary: https://en.wikipedia.org/wiki/Almgren-Chriss_model | DOI PAYWALL; wiki FREE | Impact vs timing-risk tradeoff; Helix must not size as if fills are free. |
| **Kill-switch / pre-trade risk design** | SEC Rule 15c3-5 final rule PDF: https://www.sec.gov/files/rules/final/2010/34-63241.pdf · e-CFR text: https://www.law.cornell.edu/cfr/text/17/240.15c3-5 · Practitioner kill-switch patterns: https://hftradingbook.com/risk/kill-switches | Official = FREE | Automated cancel-all + halt on loss/position/rate/data anomalies; independent of strategy process. Regulatory framing for brokers — Helix should still copy the **control hierarchy**. |

---

## 4. What to wire into Helix

Concrete checklist before any **live sizing** (research/paper enforcement first). Mark UNKNOWN where Helix repo state is unclear from this pack alone.

| # | Gate / artifact | Library or reference | Enforce before live sizing? | Status |
|---|-----------------|----------------------|-----------------------------|--------|
| 1 | **Half-Kelly (or ≤½ Kelly) hard cap** on position fraction from estimated edge; never full Kelly on backtest μ | Thorp / MacLean–Ziemba; sizing via PyPortfolioOpt/`riskfolio` Kelly options only as *upper bound research* | YES | Spec ready; Helix code path = **UNKNOWN** |
| 2 | **Walk-forward report** (rolling or anchored): IS window → select → OOS next window; stitch OOS equity; no peek | vectorbt WFO / quantstrat `walk.forward` / PortfolioTesteR | YES | Spec ready; report schema = **UNKNOWN** |
| 3 | **DSR gate**: compute Deflated Sharpe with trial count *N*, skew, kurtosis; fail if DSR p below threshold (e.g. 0.95) | Bailey & López de Prado (2014) | YES | Threshold default = **UNKNOWN** (propose 0.95; confirm) |
| 4 | **PBO / CSCV diagnostic** on candidate matrix; fail if PBO > policy (literature often treats >0.5 as reject) | Bailey et al. PBO PDF; ml4trading CPCV digest | YES | Exact Helix cutoff = **UNKNOWN** (propose reject if PBO ≥ 0.5) |
| 5 | **CPCV or purged+embargoed CV** for any ML/feature model; ban iid KFold on labels with horizon | AFML / CPCV digest | YES for ML signals | Helix ML pipeline = **UNKNOWN** |
| 6 | **Vol / GARCH sanity**: forecast σ used for targeting must be fit **causally** (expanding/rolling), not full-sample | `rugarch` / `arch` | YES if vol-target live | **UNKNOWN** |
| 7 | **Regime overlay (optional)**: HMM risk-off shrinks size; never sole entry signal without falsification | `hmmlearn` + Hamilton | OPTIONAL | **UNKNOWN** |
| 8 | **Portfolio risk budget**: CVaR / max DD / gross & net exposure caps via Riskfolio or PA metrics | Riskfolio-Lib / PerformanceAnalytics | YES | Cap values = **UNKNOWN** |
| 9 | **Execution haircut**: min fee+slippage model; reject backtests with zero costs | Almgren–Chriss doctrine (haircut proxy OK at v1) | YES | Cost model = **UNKNOWN** |
| 10 | **Kill switches (process-level)**: daily/weekly loss limit, max position, max order rate, stale-data / feed-gap halt, cancel-all then block new orders; independent monitor | SEC 15c3-5 spirit + HFT Book kill-switch patterns | YES before live | Implementation = **UNKNOWN** |
| 11 | **Trial ledger**: every optimized param/grid search increments *N* for DSR; no silent retries | DSR paper | YES | Logging schema = **UNKNOWN** |
| 12 | **Unit tests as gates**: fixture strategies that *must fail* DSR/PBO (random-walk overfit) and *must pass* seeded seasonal edge (per PBO paper examples) | Bailey et al. seasonal examples in PBO PDF | YES (CI) | Test suite coverage = **UNKNOWN** |

### Suggested fail-closed policy (draft — not code)

1. No live size > 0 unless gates **2, 3, 9, 10** pass.  
2. If ML involved, also **5**.  
3. Size = `min(HalfKelly(edgê), risk_budget, regime_mult)` with `edgê` from **OOS-only** stats.  
4. Any kill-switch trip → flat + human reset token (**UNKNOWN** auth design — out of scope).

---

## 5. Verification log / do-not-invent

| Resource | Check (2026-09-09) | Note |
|----------|--------------------|------|
| CRAN PerformanceAnalytics | WebFetch OK | v2.1.0 listed |
| CRAN quantmod | WebFetch OK | v0.4.29 |
| CRAN rugarch | WebFetch OK | index live |
| CRAN xts | WebFetch OK | index live |
| CRAN zoo | WebFetch OK | index live |
| vectorbt.dev / GitHub | Search + docs hit OK | PRO paid separate |
| backtesting.py docs | WebSearch OK | |
| zipline.ml4trading.io | WebSearch OK | |
| QuantConnect/Lean | WebFetch OK | |
| riskfolio-lib.readthedocs | WebFetch OK | |
| pyportfolioopt.readthedocs | WebFetch OK | |
| arch.readthedocs | WebFetch OK | |
| hmmlearn.readthedocs | WebFetch OK | |
| davidhbailey.com PBO PDF | WebFetch OK (full text) | Prefer this over Risk.net paywall |
| JPM DSR DOI | Metadata OK; full text PAYWALL | Use SSRN/DOI; don’t invent formulas beyond paper |
| Almgren–Chriss DOI | Metadata OK; full text PAYWALL | |
| Hamilton 1989 DOI | Metadata OK; full text PAYWALL | |
| quantstrat on CRAN | Not treated as primary CRAN install | Install path **UNKNOWN**/GitHub |
| Exact Helix repo wiring | Not inspected in this pack | All “wire” rows marked UNKNOWN where code state unknown |

**Blockers:** none for writing this pack. Full-text of some DOIs is PAYWALL (expected). No secrets requested or stored.

---

## Counts

| Bucket | Solid entries (URL + why) |
|--------|---------------------------|
| R / stats | 9 |
| Python quant | 9 |
| Math / papers / controls | 9 |
| **Total curated** | **27** |
| Wire-into-Helix checklist rows | 12 |

*End of pack — paper research only.*
