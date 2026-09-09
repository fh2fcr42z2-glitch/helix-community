---
layout: default
title: Alpha Writer NOTE
permalink: /note/
nav: note
---

# Alpha Writer NOTE

Alpha Writer is the **publish layer**: a human-paced pipeline that turns a researched disagreement into a **NOTE**. A NOTE is a lab write-up. It is not a tweet storm, not a buy list, and not an order.

**No auto-post.** X/Twitter auto-post is **DARK / off**. WordPress, if it ever exists here, is **draft-only** — a future parking spot for a NOTE, not a live CMS hammer.

Paper-only. Not financial advice. Not a broker.

## Pipeline (evidence-gated)

Hats, not private class names. One person may wear several. The **gate** still has four desks:

```
Scout  →  Researcher  →  Market Ops  →  Alpha Writer
  ↑                         ↑
 FLOW                    kill switches
 candidates               (stale BTC,
                          CB vs Kraken ≥25bp,
                          thin DEX)
```

| Hat | Job | May not |
| --- | --- | --- |
| **Scout** | Surface a candidate: FLOW rung (chain / DEX / token), three legs (tape / search / chatter), DARK list | Size a book, hide a missing wallet leg, “just post it” |
| **Researcher** | Turn the candidate into a dated thesis. Attach **evidence**. Assign a **verification level** to each claim | Quietly edit the thesis after the tape moved; fill DARK with color |
| **Market Ops** | Check tape hygiene and **kill switches**. Confirm marks would come from real bars | Flip a switch off to save a narrative; place an order |
| **Alpha Writer** | Assemble a NOTE only when claims are publishable and no switch is tripped | Auto-post to X; publish WordPress live; strip the DARK list to look confident |

Head of Desk still owns the queue. Risk may veto the paper book. Sentinel forbids live execution. Alpha Writer does not outrank any of them.

Detail on FLOW and switches: [FLOW.md](FLOW.md). Desk map: [ARCHITECTURE.md](ARCHITECTURE.md).

## Claim verification levels

Every factual sentence in a NOTE carries a level. If you cannot label it, it is **DARK**.

| Level | Meaning | May appear in a published NOTE? |
| --- | --- | --- |
| **DARK** | Not observed, not keyed, or not license-clean | Only as an explicit DARK line. Never as an implied whale, bridge, or CEX entity |
| **Observed** | One public/free source, cited, timestamped | Yes, labeled. Single-source claims stay humble |
| **Corroborated** | Two independent public sources, or two legs that actually disagree (not a blended score) | Yes, if kill switches are clear |
| **Keyed-read** | A **read-only** research key in a *private* environment made a gated port non-DARK | Only if the NOTE says the claim is **not reproducible on the free bench**. Never paste the key |
| **Blocked** | Kill switch tripped, or Market Ops / Risk said no | No. Record the block in Process; do not publish a cleaned-up version |

**Keyed-read is not a flex.** It is a warning label: the community cannot replay that sentence without the same private credential. Prefer Observed and Corroborated for anything you want another contributor to check.

Do not invent extra levels (“alpha confirmed”, “high conviction”) that skip this table.

## What a NOTE must contain

1. **FLOW rung** — chain, DEX, token, or an honest stop because wallets are DARK.
2. **Three legs** — tape, search, chatter; DARK is allowed if named ([CONCEPT.md](CONCEPT.md)).
3. **Claims table** — each claim + verification level + source.
4. **Kill-switch status** — stale BTC, Coinbase vs Kraken (≥25 bp or not), thin DEX liquidity (measured or unmeasured = tripped).
5. **DARK list** — including the standing public list (bridge netflow, labeled wallets, unpaid CEX entity flow, X auto-post, WordPress live publish).
6. **Paper action** — watch, hypothetical book, or explicit do-not-enter. Never a live instruction.
7. **Invalidation** — what would make the NOTE wrong.

If a draft is missing (4) or (5), it is not a NOTE yet. It is a Scout scrap.

## No auto-post

| Channel | Public stance |
| --- | --- |
| **X / Twitter auto-post** | **DARK / off.** No community bot, no “thread this NOTE” connector |
| **WordPress** | **Draft-only, future.** A NOTE may someday land as a draft. Live publish, scheduling, and application passwords are out of scope and must not appear in this repo |
| **This GitHub** | Issues and PRs may *link* to a NOTE draft. They must not contain keys |

Alpha Writer’s output is a document, not a distribution network. If you want distribution, copy the NOTE by hand, as a human, after the gates. That is slower on purpose.

## What Alpha Writer will not do

- Place or suggest live orders.
- Strip DARK lines to sound more certain.
- Treat a keyed-read wallet label as a public fact.
- Auto-post because a switch is green.
- Use WordPress, X, Telegram, or Discord tokens from `.env`.

Trading and swap connectors stay **off**. Read-only research keys, if any, follow [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).
