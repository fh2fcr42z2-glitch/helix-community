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
| **Desk** | What is in front of me *right now*? | Candidates, three-leg disagreement, next research action |
| **Process** | How did this idea earn a place? | Lifecycle: intake → thesis → evidence → review → paper or reject |
| **Book** | What are we hypothetically on? | Paper positions, marks, notes — no live orders |
| **Risk** | What is the book not allowed to do? | Limits, concentration, thesis expiry, veto |
| **Fleet** *(future)* | What else is running in parallel? | Isolated experiments that cannot silently join the book |
| **Lab** *(future)* | Did this idea survive a harder test? | Walk-forward, holdout, replay — still paper |
| **Alpha Writer** *(future)* | What did we learn that is worth publishing? | Write-ups, not a signal blast |

**Desk** is the attention surface. **Process** is the memory of how attention was justified. **Book** is the only place a “position” exists, and it is paper. **Risk** can say no. **Fleet** and **Lab** stay quarantined until a human process promotes a result. **Alpha Writer** publishes *method and outcome*, not an order ticket.

Nothing in this table is a trading venue.

## Data flow

The public flow is short on purpose:

```
free market APIs
        ↓
research lifecycle          (Process)
        ↓
paper book                  (Book)  ←  Risk may veto
        ↓
(future) Alpha Writer       publish what was learned
```

1. **Intake** — public, free-tier market and interest data. Today that means the free column in [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md): Coinbase, Kraken, CoinGecko, DefiLlama, DEX Screener, GeckoTerminal, Google Trends. If a feed is not in that column and no key is present, the field is **DARK**.
2. **Research lifecycle** — a Scout-shaped question becomes a dated thesis with an invalidation. Process keeps the artifacts. No silent edits to the story after the tape moved.
3. **Paper book** — optional hypothetical entry. Marks come from the same real bars as intake, or the position is marked DARK. **No synthetic fill prices.**
4. **Publish layer (future)** — Alpha Writer turns a closed research cycle into a public note. It does not place orders and it does not become a newsletter of picks.

Paid or keyed feeds (wallet identity, smart money, CEX flow, SIP, options) attach at **intake only**, behind interfaces, in private environments. They do not change the rule that the book is paper.

```
[optional keyed adapters] ──┐
                            ├─→ intake → Process → Book (paper) → Alpha Writer (future)
[free adapters] ────────────┘              ↑
                                         Risk
                                         Sentinel (nothing live)
```

## Specialist roles (conceptual)

These are **hats**, not an org chart and not a promise of private class names. A single contributor may wear more than one. Implementations should keep the *responsibilities* separable even if the code is small.

### Head of Desk

Owns the queue. Decides what gets time this week, what is parked, and what is never allowed to become a paper position. Protects the desk from turning every viral coin into a thesis. Does not “approve live risk” — there is no live risk in this framing.

### Search / Scout

Hunts disagreements across tape, search, and chatter. Surfaces candidates with sources and a DARK list. Does not size the book. Does not hide a missing leg behind a blended score.

### Process

Keeps the lifecycle honest. Every paper entry should be traceable to a thesis, evidence, and a review. Process fights narrative drift: if the reason changed, that is a new thesis, not a quiet edit.

### Book

The paper ledger. What we are hypothetically on, when it was opened, where the mark comes from, and the note that goes with it. Book never talks to a live order API. If someone adds a broker adapter later, Book still does not become that adapter.

### Risk

Constraints on the paper book: gross, concentration, single-name, thesis age, drawdown of the *hypothetical* ledger. Risk may veto an entry that Process already likes. Paper risk is still risk to the research process — a book that can do anything teaches nothing.

### Sentinel

The permanent execution gate. **Sentinel’s job is to keep Helix paper-first**, including in futures where a broker or CEX key exists in some private environment. Community code must assume Sentinel can block anything that looks like `submit`, `create_order`, or “just a test live pin.” There is no community path to unsupervised live trading.

### Alpha Writer *(future)*

Publishes after the cycle, not during it. Audience is other researchers. Output is a note: question, data, disagreement, result, what stayed DARK. Not a blast of tickers.

### Fleet / Lab *(future)*

Fleet: many small research runs that cannot write the main book. Lab: harder validation (walk-forward, holdouts). Promotion is a Process event, not a cron job that “goes live.”

## Interface discipline

Community adapters should look like this, even if the private code does not:

- **Ports** — `Tape`, `SearchInterest`, `Chatter`, later `WalletIdentity`, `CexFlow`, `EquitySip`, `OptionsFlow`.
- **One vendor per adapter** — `coingecko_tape.py` is fine; `everything.py` is not.
- **Mocks in tests** — the port is satisfied by a fixture. CI never holds a vendor key.
- **DARK on failure** — timeout, 401, missing key, unsupported pair: return a labeled empty/DARK, do not interpolate a bar.
- **No secrets in objects that get logged.**

Exact type names are up to the language of the contribution. The rule is the seam, not the filename.

## What stays out of this repo

- Private source, configs, and `.env` files from helix-cx
- Vendor keys, cookies, session tokens, wallet seeds
- Claims about unpublished performance
- Encouragement to flip Sentinel off

If you need a capability that is DARK, document it in an issue as a **needed adapter**, not as a request for someone else’s key. See [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).
