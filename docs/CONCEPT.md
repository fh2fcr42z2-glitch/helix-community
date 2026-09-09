---
layout: default
title: Social arbitrage
permalink: /concept/
nav: concept
---

# Social arbitrage

Helix’s research lens is a **three-way disagreement**.

| Leg | What it is | What it is not |
| --- | --- | --- |
| **Price tape** | Trades and quotes that actually printed — CEX, DEX, later a licensed equity tape | A forecast, a “fair value,” or a synthetic bar |
| **Search interest** | People querying — Google Trends and similar public search series | A news firehose or a paid alternative-data contract |
| **Social / consumer chatter** | What people say and pass around — public social and consumer talk | A guaranteed leading indicator |

**Social arbitrage**, as Helix uses the phrase, is the study of that gap. It is not a promise that the gap closes, that you can harvest it, or that a model has found it. It is a way to write a thesis:

> The tape says X. Search says Y. Chatter says Z. Those cannot all be the same story. Here is what would change my mind.

## Why the legs diverge

They measure different clocks and different people.

- **Tape** updates when someone is willing to transact. Illiquid coins can look asleep while Twitter is loud. A thin book can print a violent candle while nobody is searching the name.
- **Search** updates when someone is willing to type. It is often late to a professional move and early to a retail one. Trends is coarse, delayed, and geography-skewed. That is still information — as long as you label the coarseness.
- **Chatter** updates when someone is willing to talk. It is noisy, copied, and sometimes paid. Volume of talk is not the same as informed talk.

A desk that collapses the three legs into one “sentiment score” has already thrown away the object of study. Helix keeps them separate long enough to see the disagreement.

## Worked shape of a thesis (paper only)

A community paper idea should name all three legs, even if one is DARK.

1. **Instrument** — what market, what pair, why that one.
2. **Tape** — last real bars you would trust; what “moved” means.
3. **Search** — which query or topic; what “interest rose” means.
4. **Chatter** — which public venues; what you refuse to count (bots, copied headlines).
5. **Disagreement** — one sentence: who is early, who is late, who is absent.
6. **Invalidation** — what print, what Trends print, or what silence kills the thesis.
7. **Paper action** — a hypothetical book entry, or an explicit *do not enter*.
8. **DARK list** — which legs you could not observe. Missing data is part of the result.

Example skeleton (fictional names, not a recommendation):

> Pair: `AAA/USD` on a public CEX. Tape: 24h volume collapsed while price held. Search: `AAA` Trends still rising week-over-week. Chatter: Telegram forwards repeating last week’s unlock rumor. Disagreement: search and talk assume a story the tape has stopped sponsoring. Invalidation: a real volume bar back through the 30-day median, or Trends rolling over. Paper action: none — watch list only. DARK: wallet flow, exchange inflow.

That last line matters. If you cannot see wallets or CEX flow, you do not get to imply them.

## Research / paper-only

Helix is a **research and education** project.

- No live orders.
- No “hot keys.”
- No performance marketed as return.
- Paper book marks are hypothetical. They train process, not a track record for allocation.

If a write-up reads like a call to buy or sell, rewrite it until it reads like a lab note.

This is **not financial advice**. Markets can and do remain disagreed longer than a thesis can stay solvent — even a paper one. Helix will not tell you otherwise.

## Crypto-first, equities later

The public CX direction is **crypto first**:

- Public CEX and DEX tapes are reachable without a SIP license.
- Search + chatter around coin names is observable on free tools.
- The desk can stay honest with a short free-tier list (see [sensitive integrations](SENSITIVE-INTEGRATIONS.md)).

**Equities are a sidecar.** A full US tape (SIP), options flow, and broker connectivity sit behind licenses and keys. They are out of scope for a free public bench. Mentioning Interactive Brokers or Tiingo in the capability matrix means “this is what a keyed sidecar *would* unlock,” not “equities are live.”

## What Helix will not pretend

- That Google Trends is high-frequency.
- That CoinGecko replaces a matching engine.
- That DEX screenshots are wallet identity.
- That a mock in a unit test is a production feed.
- That the private build’s unpublished adapters exist for you to call.

If you want to help, write adapters and paper theses that survive those sentences. Start at [CONTRIBUTING.md](CONTRIBUTING.md).
