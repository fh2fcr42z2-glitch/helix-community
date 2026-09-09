# Helix crew handoff (signal pipeline)

Source inspiration: public multi-agent trading crew writeups (@immortalhowwl / GPTHEIST-style roles).  
**Use the operating rules. Do not use character cosplay or claimed PnL as evidence.**

## Verified vs DARK
- **Use:** one job per agent, strict handoffs, veto gates, don’t-chase discipline, human approval for money.
- **DARK / ignore as proof:** any specific PnL story ($52 → $11k), “Robinhood overnight” claims, or “no human touched the mouse.” Community notes flag custom dashboards and unverified wallets. Never cite those numbers as Helix performance.

## Helix role map (one job each)

| Helix lane | Inspiration label | One job |
|---|---|---|
| Tape / Scout | TOKYO | Find fresh names where **volume builds before price**; pass evidence, not vibes |
| Sentinel / Risk | PALERMO | **Block** entries without enough liquidity for a safe exit |
| Plan / Setup | BERLIN | Write **exact conditions** that reset or re-arm the setup |
| Entry timing | RIO | Catch **pullbacks**, mark **invalidation**; never chase a flying chart |
| Alpha / Social | DENVER | Compare X/Telegram mentions to **on-chain volume**; filter paid noise |
| Data quality | LISBON | Reject **stale** snapshots (holders, liquidity, bars); send setup back |
| Sizing | STOCKHOLM | Test pool depth / slippage; **size to fit the exit** |
| Brief | NAIROBI | Compress cleared signals into **one brief** for the decision gate |
| Ops log | HELSINKI | Log every position, exit condition, and change |
| Chief of Staff | PROFESSOR | One front door; return **one final report**; do not do specialist work |

## Five non-negotiable rules
1. **One owner per output.** Contributors OK; one named owner.
2. **Handoffs via files/evidence**, not memory alone (path + decision + source).
3. **Evidence travels with the claim** (link + as-of). No date/link → DARK.
4. **Prepare ≠ execute.** Sending, spending, live orders stay behind **human approval**.
5. **Every veto names the failed criterion** and the owner to fix it. “Bad” is not a veto.

## Signal path (improve Helix)
```
Scout (vol>price) → Liquidity veto → Setup conditions
  → Pullback + invalidation → Social vs on-chain filter
  → Freshness check → Size to exit → One brief
  → Ops log → CoS report → human go/no-go
```
A signal advances **only after every filter**. If the chart flies without the crew, **do not chase** — wait until the original setup returns.

## What to add next (helpful, not confusing)
- Wire these as named gates in Fleet OS / Ops Ridge (real counts only; DARK if unverified).
- Reject handoffs missing: owner, evidence URL/as-of, invalidation, exit liquidity note.
- Keep Money Heist names out of the product UI; Helix lane names above are enough.

## Do not tell Grok / agents
- That unsupervised live trading is allowed.
- That any viral PnL post is a backtest or live result for Helix.
- To invent whale labels, holder stats, or mention counts when sources are missing.
