---
layout: default
title: Five-force lens
permalink: /forces/
nav: note
---

# Alpha Writer: five-force lens

Helix Alpha Writer may **tag** a NOTE with Ray Dalio’s public **five-force** lens (money/credit, internal order, external order, nature, technology). **Reader** and **Chart bot** use the same six Grok strings on JSON (`debt_cycle` … `DARK`). The lens is a **labeling aid**, not a forecast engine and not a buy list.

Paper-only. Not financial advice. Not a broker. **DARK if unclear. Evidence required.**

This is not a dump of *Principles* or any private Grok chat. Dalio’s names belong to him; Helix only uses the five buckets as tags.

## Tags

A NOTE may carry zero or more of:

| Tag | Force (plain language) | Helix use |
| --- | --- | --- |
| `force:credit` | Money, credit, debt, markets | Tape/FLOW disagrees with a credit or liquidity story |
| `force:internal` | Internal order / conflict | Politics, policy, social split showing up in search/chatter |
| `force:external` | External order / conflict | Geopolitics, sanctions, cross-border flow **without inventing wallets** |
| `force:nature` | Acts of nature | Disaster, pandemic, climate shock as a cited event |
| `force:tech` | Human inventiveness / technology | Protocol, hardware, or model-shift as a cited change |

Tag the **NOTE** (or the Reader JSON / Chart bot sidecar), not the whole desk. Crypto-first CX still climbs [FLOW.md](FLOW.md) first. Forces do not replace tape / search / chatter. Headline ingest: [READER.md](READER.md).

## DARK if unclear

If you cannot say **which** force, or the force is a vibe, the tag is **`force:DARK`**. Do not pick `credit` because the coin moved. Do not pick `external` because Twitter said “war.”

Multiple tags are allowed when **each** has evidence. A five-tag NOTE with one cite is over-tagged — strip to DARK.

## Evidence required

Same ladder as [ALPHA-WRITER.md](ALPHA-WRITER.md):

- Every force tag needs a **claim + verification level + source**.
- Missing source → **DARK**, not a quieter font.
- Kill switches still apply (stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX, geo 451/403).
- No auto-post. World Monitor (below) does not fire X.

A tagged NOTE still needs FLOW rung, three legs, DARK list, paper action, invalidation.

## Chart bot and Reader (same five buckets, Grok strings)

Chart shots / Chart bot theses and **Reader JSON** use the **Grok pack strings** on `primary_force`, not the `force:` prefix. Same five buckets. **Unclear → `DARK`. Never invent macro.** Reader still runs a rhetoric/myth filter and a tape check after the tag — [READER.md](READER.md).

| Chart bot / Reader / Grok | This page (NOTE) |
| --- | --- |
| `debt_cycle` | `force:credit` |
| `internal_order` | `force:internal` |
| `geopolitics` | `force:external` |
| `nature` | `force:nature` |
| `inventiveness` | `force:tech` |
| `DARK` | `force:DARK` |

Readable cards (`levels`, `invalidation`, `thesis_blurb`) and the learning loop: [CHART-BOT.md](CHART-BOT.md) · [TECHNICAL-ANALYSIS.md](TECHNICAL-ANALYSIS.md). Grok copy-paste: [grok/GROK-ALPHA-FIVE-FORCES.md](grok/GROK-ALPHA-FIVE-FORCES.md). Headline judge: [READER.md](READER.md) · [grok/GROK-READER-HEADLINE.md](grok/GROK-READER-HEADLINE.md).

## World Monitor MCP (future, optional)

**World Monitor MCP** is a **future evidence substrate** for force tags — not in Helix now, not a free firehose.

| Stance | Meaning |
| --- | --- |
| **Optional** | A NOTE is valid with Trends, news RSS (Top-to-add), and cited public pages |
| **Pro / API** | If it exists later, expect a **paid or keyed** MCP/API in a *private* env |
| **DARK here** | Unpaid, unkeyed, or unwired = no World Monitor claims |
| **No secrets** | Never paste MCP tokens, Pro cookies, or prompt dumps into this repo |

Named ≠ wired. Treat it like Unusual Whales API: a wishlist row, not Coinbase.

Scout catalog: [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md). Memory / cowork: [DATA-AND-MEMORY.md](DATA-AND-MEMORY.md).
