# Helix research loop (process only)

Inspiration: public writeups on the quant cycle (e.g. @antpalkin).  
**Use the loop. Ignore product promo links, dollar claims, and “ships today” marketing.**

## The six stages
1. **Research** — find something worth testing (parallel specialists; no cross-talk mid-run; don’t anchor on the crowd price if the job is discovery).
2. **Code** — turn the idea into executable entry/exit/size/risk.
3. **Backtest** — sealed out-of-sample the builder doesn’t touch; walk-forward; **Deflated Sharpe**; a breaker whose job is to kill the idea (e.g. 2× costs, worst regimes).
4. **Live** — broker/kill switch/position state. **Kill switch lives in code, never only in a prompt.**
5. **Post-mortem** — every decision logged with reason; critic surfaces repeated failure patterns; **preregister** expected outcome before the test (no moving goalposts).
6. **Fine-tune** — fold lessons into a **hypothesis graph** (what failed, where, in which regime). Negative results are first-class. Next cycle must not restart from ignorance.

## Helix constraints (do not confuse ops)
- Stages 1–3 + paper 4 are in scope for agents.
- Real live (stage 4 with money) needs **explicit Call Me X approval** and evidence gates.
- Stage 6 stores failures in warehouse / memory with `quality_flag` — never rewrite history.
- Risk limits and kill switches are **code/config**, not chat suggestions.
- Do not import third-party SaaS as required deps from a tweet; map ideas onto Helix CX + FREE sources first.

## Fit with crew handoff
Crew gates (liquidity veto, freshness, don’t-chase, one brief) sit **inside** stages 1 and 4 prep. See [CREW-HANDOFF.md](./CREW-HANDOFF.md). Artifact promotion (idea → cowork note → Scout INVENTORY flag → CoS Cloud Agent PR → warehouse/Fleet) is [ENGINE-FLOW.md](./ENGINE-FLOW.md) — skip/veto first-class; Grok reads community `main` only.
