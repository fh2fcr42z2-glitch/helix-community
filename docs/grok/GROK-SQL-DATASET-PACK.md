# Helix → Grok prompt pack: SQL datasets & growing needs

Copy any block into Grok. Replace `{...}` placeholders. Hard rules for every prompt: **never invent rows**; use `NULL`/`DARK` for unknowns; no secrets in SQL or docs; Helix is **live-capable** but agents must not place orders unless X explicitly approves.

---

## 1) Warehouse bootstrap (SQLite / DuckDB)

```
You are Helix Data Architect. Design a versioned SQL warehouse for a live-capable crypto research desk (CX tape, FLOW, liquidations, funding/OI, Alpha Writer evidence, paper→live gates).

Requirements:
- Engine: DuckDB primary + SQLite fallback
- Schemas: raw_*, staging_*, mart_*, meta_*
- Facts: bars_1m, bars_1h, quotes_snapshot, funding_rate, open_interest, liquidations, defi_tvl, dex_volume, fear_greed, paper_fills, live_orders (empty until approved), evidence_claims
- Dimensions: venue, symbol, chain, source, quality_flag (PASS|WARN|FAIL|DARK)
- Every fact row needs: source, fetched_at, asof_ts, quality_flag
- Geo-blocked venues (Binance 451 / Bybit 403) must store DARK events, not fake prices
- Migrations as numbered SQL files

Deliver: ERD in markdown, CREATE TABLE DDL, 5 example quality queries, and a README for /data/warehouse/.
Do not invent sample market prices — use clearly marked EXAMPLE-ONLY synthetic rows if needed for DDL demos.
```

---

## 2) Dataset quality gates

```
Define SQL-enforced dataset quality gates for Helix free sources (Coinbase, Kraken, OKX, Hyperliquid, DefiLlama, DEX Screener, Fear&Greed, liq venues).

For each source produce:
1) freshness SLA (max age)
2) completeness checks (null rates, symbol coverage)
3) cross-venue divergence (≥25bp Coinbase vs Kraken on majors)
4) schema drift detection
5) FAIL → mark DARK and alert meta.quality_events

Output: SQL views `mart.quality_daily` + a checklist Helix Sentinel can read.
No invented metrics — formulas only.
```

---

## 3) ETL from free APIs → tables

```
Write an ETL plan (Python or SQL+http) from FREE APIs into Helix marts:
- Coinbase/Kraken quotes & candles
- OKX/Bitget/Gate/HTX liquidations (Binance/Bybit may geo-fail → log DARK)
- Hyperliquid metaAndAssetCtxs (funding/OI)
- DefiLlama TVL/DEX overview
- alternative.me fear&greed

Constraints: no API keys required for P0; rate-limit politely; idempotent upserts on (venue,symbol,asof_ts); store raw JSON in raw.* for replay.
Deliver: table list, upsert keys, pseudocode, and backfill strategy for 30/90/365 days where free history exists.
```

---

## 4) Walk-forward & Deflated Sharpe tables

```
Design SQL marts for live-confidence research (not toy paper forever):
- mart.strategy_runs (params, universe, start/end, seed)
- mart.walk_forward_folds (train_start/end, test_start/end, embargo)
- mart.fold_metrics (sharpe, deflated_sharpe, max_dd, hit_rate, n_trades)
- mart.pbo_estimates (probability of backtest overfitting)
- mart.kelly_sizing (half-kelly, caps, sleeve limits)

Include SQL that computes simple Sharpe from returns table; document Deflated Sharpe inputs (n_trials, skew, kurtosis) as columns to be filled by Python/R — do not fake DS values.
Explain how FAIL folds block live promotion.
```

---

## 5) Flexible memory ↔ SQL bridge

```
Helix has layered memory: agent profile/log, project helix memory, INVENTORY.md, cowork notes, and SQL warehouse. Propose a bridge so growing needs stay flexible:

1) What belongs in prose memory vs SQL vs files
2) `meta.memory_links` table: (memory_key, sql_object, reason, updated_at)
3) How Grok/Cowork should promote a finding: note → inventory → DDL → ETL → mart
4) Retention: hot (7d), warm (90d), cold (Parquet archive)
5) Privacy: never store API keys, cookies, or account numbers in SQL

Deliver a short operating manual X can paste into Helix team instructions.
```

---

## 6) Question→SQL for the Fleet desk

```
Given Helix Fleet OS answering user questions with citations, design:
- `mart.question_log` (question, parsed_intent, sql_used, sources, dark_fields, answer_ts)
- Patterns for: "what's funding on BTC across venues?", "any liq cascade in last hour?", "is Coinbase-Kraken diverged?", "what is DARK right now?"
Return 8 parameterized SQL templates with :symbol :venue :lookback parameters.
If data missing, SQL must return DARK/empty — never guess.
```

---

## 7) Growing needs / migration prompt

```
Helix needs will grow (options via Deribit, equity sidecar, live brokers later). Write a migration playbook:
- Additive migrations only
- Feature flags: enable_live_orders default false
- How to add a new venue adapter → raw → staging → mart without breaking Fleet panels
- Contract tests: row count smoke, null checks, divergence checks
Produce a checklist Grok can re-run each time we add a source.
```

---

## 8) R + Python handoff from SQL

```
From Helix SQL marts, specify export views for:
- R: xts-friendly CSV (timestamp, open, high, low, close, volume, venue)
- Python: Parquet partitions by date/venue for vectorbt / arch / hmmlearn
Include column dictionaries and a note on aligning funding timestamps (8h vs 1h venues).
No fake datasets — schema + empty examples only.
```

---

## Meta prompt (use when stuck)

```
Helix context: live-capable crypto desk; free data first; DARK over invention; Scout owns INVENTORY; Cowork owns deep research; Chief of Staff wires PRs; no unsupervised live orders.
Task: {TASK}
Constraints: {CONSTRAINTS}
Success: {SUCCESS}
First list unknowns as DARK, then propose SQL/ETL/tests, then minimal DDL.
```

---

## Helix wiring (don’t duplicate in prompts)

| Concern | Owning artifact |
|---------|-----------------|
| TS walk-forward / DSR / Kelly gates | `/workspace/helix-cowork/briefs/brief-risk-gates-wf-dsr-kelly.md` |
| Optional `data/` DuckDB/SQLite enablement | `/workspace/helix-cowork/briefs/brief-data-warehouse.md` |
| Memory layer cake | `/workspace/helix-cowork/notes/memory-flexibility.md` |
| Expanded Cowork prompt mirror | `/workspace/helix-cowork/prompts/grok-sql-dataset-pack.md` |
