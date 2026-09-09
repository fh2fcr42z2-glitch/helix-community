---
layout: default
title: Architecture
permalink: /architecture/
nav: architecture
---

# Architecture (public-safe)

This is a **map of names and responsibilities**, not a dump of the private tree. If a box is not listed here, do not assume it exists. If a box *is* listed here, do not assume the private build implements it the way you would.

The [private implementation](https://github.com/fh2fcr42z2-glitch/helix-cx) is closed. Community work should target **interfaces and docs**, not reverse-engineering that repo.

## Desk surfaces

Think of Helix as a small research floor. Each surface answers a different question.

| Surface | Question it answers | Community-visible job |
| --- | --- | --- |
| **Desk** | What is in front of me *right now*? | FLOW rung, three-leg disagreement, next research action |
| **Process** | How did this idea earn a place? | Scout → Researcher → Market Ops → paper book or reject |
| **Book** | What are we hypothetically on? | Paper positions, marks, notes — no live orders |
| **Risk** | What is the book not allowed to do? | Limits, vetoes, kill switches (research halts — not live orders) |
| **Fleet** *(future)* | What else is running in parallel? | Isolated experiments that cannot silently join the book |
| **Lab** *(future)* | Did this idea survive a harder test? | Walk-forward, holdout, replay — still paper |
| **Alpha Writer** | What did we learn that is worth publishing? | An evidence-gated **NOTE** — not a signal blast, not auto-post |

**Desk** is the attention surface. **Process** is the memory of how attention was justified. **Book** is the only place a “position” exists, and it is paper. **Risk** can say no. **Fleet** and **Lab** stay quarantined until a human process promotes a result. **Alpha Writer** publishes a **NOTE** (method, evidence, DARK list) — never an order ticket and never an auto-post. See [ALPHA-WRITER.md](ALPHA-WRITER.md).

Nothing in this table is a trading venue.

Crypto-first CX reads markets through **FLOW** before it argues about a coin: chain → DEX → token → wallets (DARK). See [FLOW.md](FLOW.md).

## Data flow

Crypto-first intake is **FLOW**, then the three social-arbitrage legs, then paper, then a NOTE:

```
FLOW  chain → DEX → token → wallets DARK
        + tape / search / chatter   (free APIs)
        ↓
Scout → Researcher → Market Ops     (Process)
        ↓
paper book                          (Book)  ← Risk + kill switches
        ↓
Alpha Writer NOTE                   no auto-post; WordPress draft-only future
```

1. **FLOW intake** — climb [FLOW.md](FLOW.md). Free rung data: DefiLlama (stables / TVL / DEX vol), Llama volume + screener pair, token board + trending, plus CEX tapes and Trends. If a feed is not in the free column of [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md), the field is **DARK**.
2. **Scout → Researcher** — a candidate becomes a dated thesis with evidence and a verification level per claim. Process keeps the artifacts. No silent edits after the tape moved.
3. **Market Ops** — kill switches (stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX liquidity) and real-bar marks. Switches halt *promotion*, not live orders (there are none).
4. **Paper book** — optional hypothetical entry. Marks come from the same real bars as intake, or the position is marked DARK. **No synthetic fill prices.**
5. **Alpha Writer NOTE** — evidence-gated write-up. **No X auto-post.** WordPress, if ever, is draft-only. See [ALPHA-WRITER.md](ALPHA-WRITER.md).

Facts the desk must remember (INVENTORY, cowork notes, SQL warehouse, Parquet cold) follow [DATA-AND-MEMORY.md](DATA-AND-MEMORY.md): **DARK > invention**, no secrets in any layer.

Read-only research keys (wallet labels, Llama Pro bridge netflow, unpaid CEX entity feeds) attach at **intake only**, behind interfaces, in private environments. They do not change the paper book, Sentinel, or the no-auto-post rule. **Swap and trading connectors stay off.**

```
[optional read-only keys] ──┐
                            ├─→ FLOW + legs → Scout → Researcher → Market Ops
[free adapters] ────────────┘                              ↑
                                                    Risk, kill switches
                                                    Sentinel (nothing live)
                                                                   ↓
                                                         Alpha Writer NOTE
```

## Specialist roles (conceptual)

These are **hats**, not an org chart and not a promise of private class names. A single contributor may wear more than one. Implementations should keep the *responsibilities* separable even if the code is small.

### Head of Desk

Owns the queue. Decides what gets time this week, what is parked, and what is never allowed to become a paper position. Protects the desk from turning every viral coin into a thesis. Does not “approve live risk” — there is no live risk in this framing.

### Search / Scout

Hunts disagreements across tape, search, and chatter, on a named **FLOW** rung. Surfaces candidates with sources and a DARK list. Does not size the book. Does not hide a missing wallet leg behind a blended score.

### Free Market Data Scout

Continuously catalogs sources as **FREE / FREE-TIER / PAID / DARK**. Owns the **living inventory** in [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md) — FREE in Helix now vs Top-to-add. Does not invent data. Does not collect keys. Delayed dashboards and geo 451/403 are not firehoses. Wallets, bridges, and entity labels stay DARK without a verified free source.

### Researcher

Turns a Scout scrap into a thesis. Attaches evidence and a **verification level** to each claim ([ALPHA-WRITER.md](ALPHA-WRITER.md)). If the reason changed, that is a new thesis, not a quiet edit.

### Market Ops

Tape hygiene and **kill switches** before anything is promoted to the paper book or a NOTE. Owns stale BTC, Coinbase-vs-Kraken ≥ 25 bp, and thin DEX liquidity as *research halts*. Does not trade.

### Process

Keeps the lifecycle honest. Every paper entry should be traceable to a thesis, evidence, and a review. Process fights narrative drift: if the reason changed, that is a new thesis, not a quiet edit.

### Book

The paper ledger. What we are hypothetically on, when it was opened, where the mark comes from, and the note that goes with it. Book never talks to a live order API. If someone adds a broker adapter later, Book still does not become that adapter.

### Risk

Constraints on the paper book: gross, concentration, single-name, thesis age, drawdown of the *hypothetical* ledger. Risk may veto an entry that Process already likes. Paper risk is still risk to the research process — a book that can do anything teaches nothing.

**Kill switches** (Market Ops; paper promotion only): stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX liquidity. Full table: [FLOW.md](FLOW.md). They never place orders.

### Sentinel

The permanent execution gate. **Sentinel’s job is to keep Helix paper-first**, including in futures where a broker or CEX key exists in some private environment. Community code must assume Sentinel can block anything that looks like `submit`, `create_order`, swap/router calls, or “just a test live pin.” **Swap and trading connectors stay off.** There is no community path to unsupervised live trading.

### Alpha Writer

Publishes after the cycle, not during it. Output is a **NOTE**: FLOW rung, claims with verification levels, kill-switch status, DARK list, paper action. Audience is other researchers. **No auto-post** to X. WordPress is draft-only future. Not a blast of tickers. Full page: [ALPHA-WRITER.md](ALPHA-WRITER.md).

### Fleet / Lab *(future)*

Fleet: many small research runs that cannot write the main book. Lab: harder validation (walk-forward, holdouts). Promotion is a Process event, not a cron job that “goes live.”

## Interface discipline

Community adapters should look like this, even if the private code does not:

- **Ports** — `Tape`, `SearchInterest`, `Chatter`, `ChainFlow`, `DexVolume`, `TokenBoard`; later `FundingOI` (usually DARK / PAID); equity-sidecar `OptionsEod`; gated read-only `WalletIdentity`, `CexFlow`, `WhaleFlow`. No `Swap` / `CreateOrder` ports in this community.
- **One vendor per adapter** — `coingecko_tape.py` is fine; `everything.py` is not.
- **Mocks in tests** — the port is satisfied by a fixture. CI never holds a vendor key.
- **DARK on failure** — timeout, 401, missing key, unsupported pair: return a labeled empty/DARK, do not interpolate a bar.
- **No secrets in objects that get logged.**

Exact type names are up to the language of the contribution. The rule is the seam, not the filename.

## What stays out of this repo

- Private source, configs, and `.env` files from helix-cx
- Vendor keys, cookies, session tokens, wallet seeds
- Private Grok chats / SQL prompt dumps
- Claims about unpublished performance
- Encouragement to flip Sentinel off

If you need a capability that is DARK, document it in an issue as a **needed adapter**, not as a request for someone else’s key. See [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).
