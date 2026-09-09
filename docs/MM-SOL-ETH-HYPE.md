# Helix Market Maker — SOL / ETH / HYPE desk map

Inspiration: public six-agent Solana MM + six-lane discovery writeups (@solst1ne and similar).  
**Use the desk map. PnL claims stay DARK — not Helix evidence.**

This page is the **multi-sleeve** map for Helix Market Maker. Canonical rails stay in [MARKET-MAKER.md](./MARKET-MAKER.md): LIVE-authorized (X 2026-09-09), `fee_income` only, principal locked, venue/liq/holders/fees DARK → block, kill in **code**. CX wiring lives on helix-cx PR #1.

## Sleeves (three books, one process)

| Sleeve | Stance | Why | Adapter truth |
|---|---|---|---|
| **SOL** | **Primary** | Lower fees — cancel/replace is cheap enough for a real quote loop | Solana DEX/CEX tape may be FREE or Top-to-add; still fail-closed if the *venue for this pair* is DARK |
| **ETH** | **Try-now** | Wider spread **and** an explicit **gas budget**. Do not run a SOL-tight loop on Ethereum gas | Public ETH tape exists; gas / priority-fee as-of is required or the sleeve SKIP/DARK |
| **HYPE** | **Third sleeve DARK** | Hyperliquid until a mocked adapter exists | [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md): Hyperliquid is Top-to-add. **Named ≠ wired.** No stub book, no stub fills |

Do not collapse the three sleeves into one “crypto MM” ledger. Each sleeve has its own pair policy, journal prefix, and DARK list. Viral SOL PnL is not a reason to light HYPE.

## Six MM roles → Helix owners

One job each. Inspiration labels stay out of the product UI.

| Inspiration role | Helix owner | One job |
|---|---|---|
| **Researcher** | **Tape / Alpha** | Name the pair and the disagreement (tape vs search vs chatter). Pass evidence, not a quote. |
| **Analyst** | **Pricing** | Fair-value / mid / skew **inputs**. Never posts. Never cancels. Missing mid → DARK → no quote. |
| **Quoter** | **MM** | Two-sided quotes from Pricing + PairProfile. Size from `fee_income` only. Risk can veto. |
| **Executor** | **Code fast path** | Cancel, replace, kill, pull. **Not an agent.** Milliseconds, flags, not prompts. |
| **Risk** | **Sentinel / kill** | Inventory, toxic-flow, kill switch. **Veto beats quoter.** Kill ON → code stops new entries. |
| **Observer** | **Ops / Chief of Staff** | Journal, as-of, sleeve status, one brief. Does not quote. Does not “fix” a kill in chat. |

Crew handoff names (Sentinel / Sizing / Ops) still apply. See [CREW-HANDOFF.md](./CREW-HANDOFF.md).

## Hard split: fast loop vs slow loop

Agents do not sit in the cancel path.

| Loop | Who | Allowed | Forbidden |
|---|---|---|---|
| **Fast** | **Code** | Cancel/replace, inventory skew, toxic-flow pull, kill ON → stop new entries | LLM in the hot path; “please stop” as the only kill; stub fills; debiting `principal` |
| **Slow** | **Agents** | Pair selection, PairProfile updates, spread/gas policy, Scout inventory, post-mortem | Sending an order, widening “in a minute,” mixing sniper tickets into the MM journal |

**Risk veto beats quoter.** A PASS quote that fails Sentinel, kill, vault, liquidity, holders, venue, or gas-budget is not a quote. The fast path pulls; the slow path writes *why*.

### Toxic flow

Informed flow that picks off resting quotes is **adverse selection**, not alpha to chase.

Helix handling (code, then journal):

1. **Detect** — fill rate vs mid move, one-sided hits, or inventory racing the tape. If the detector is unmeasured, treat toxic as **on** (fail-closed).
2. **Widen or pull** — ETH widens first (gas is expensive); SOL may pull and re-post; HYPE does neither until the adapter is LIVE.
3. **Cut size** — `size_basis=both` still; never a flat bet to “win it back.”
4. **Kill** — persistent toxic → kill ON. Code stops new entries. Observer logs the trip. Quoter does not argue.

Do not invent a toxic-flow score. Unmeasured → DARK → conservative (pull / skip), not “assume healthy.”

## Pair policy (per sleeve)

Same LIVE rails as [MARKET-MAKER.md](./MARKET-MAKER.md). Extra constraints per sleeve:

| Policy | SOL (primary) | ETH (try-now) | HYPE (DARK) |
|---|---|---|---|
| Spread | Tight enough that fees + adverse selection still fit `fee_income` | **Wider** than SOL by policy — gas is part of the spread | No quotes |
| Size | `size_basis=both` (last_close + depth_cap); `fee_income` only | Same, **and** size must fit the **gas budget** (not only depth) | n/a |
| Cancel/replace | Expected; cheap fees are why this is primary | Budgeted; do not churn the book when gas as-of is stale | n/a |
| Gas / fees | Venue fees in gate; missing fee source → SKIP | **Gas budget required** (as-of + source_id). Over budget → SKIP, never “eat principal” | n/a |
| Venue | DARK → block | DARK → block | **DARK until adapter + mock** → block |
| LaunchGate | liq + holders; stale/missing → DARK → block | Same | Same rule would apply *after* adapter; until then the sleeve does not start |
| Journal | `sleeve=SOL` | `sleeve=ETH` | `sleeve=HYPE` status DARK only — no fake ENTER |

Kill OFF → may rotate **that sleeve**. Kill ON → code stops new entries **on that sleeve** (and may halt all MM if the strip says so). Principal stays read-only on every sleeve.

## Scout venue grades (2026-09-09)

Public snapshot of **which books the Scout can actually read** for these sleeves. Grades are PASS / WARN / FAIL-DARK — **not** a depth table, **not** a quote, **not** “wired in Helix.” Full write-up lives on the desk box (`helix-market-data` / `INVENTORY`). **Do not invent numbers here** to fill a hole.

Scout grade ≠ adapter. A PASS venue still **blocks** if that pair’s venue is DARK in the journal. **HYPE stays sleeve DARK until a mocked Hyperliquid adapter** even though the public book is WARN.

| Grade | Venue | Honest note |
|---|---|---|
| **PASS** | **SOL CLOB** — Phoenix Eternal official L2 REST/WS | Perps book — **not** a spot AMM |
| **PASS** | **ETH quote depth** — Coinbase + Kraken L2 | Public CEX L2 already in the Scout catalog |
| **PASS** | **ETH gas** — public RPC `eth_gasPrice` / `eth_feeHistory` (+ Alchemy **FREE-TIER**) | Read-only fee as-of. Missing/stale gas → SKIP, never eat principal |
| **WARN** | **SOL AMM** — Orca mid+balances (no L2); Meteora mid+reserves; Raydium **1–5 min stale** | Marks / inventory context — **not** live MM L2 |
| **WARN** | **HYPE** — Hyperliquid `l2Book(HYPE)` | FREE, no key; **shared-IP 429** risk → WARN, not PASS |
| **FAIL / DARK** | Blocknative gas (sunset), dead gas stations, scrapers | Do not backfill gas or depth from these |

**Sleeve primaries** (where to look first — still fail-closed):

- **SOL CLOB** → Phoenix
- **SOL AMM marks** → Orca (+ Helius)
- **ETH** → Coinbase / Kraken + RPC gas
- **HYPE** → Hyperliquid `l2Book` with IP hygiene

No BBO, no size ladder, no invented mid. If the desk-box write-up is missing, the field is DARK.

## Discovery / sniper six lanes — separate from MM

The inspiration pack also describes a **six-lane discovery** (launch / volume-before-price / LP quality / social-vs-tape / wallet-copy / cross-venue dislocation — names vary). Helix may research those lanes. **They are not Market Maker.**

| | MM journal | Discovery / sniper journal |
|---|---|---|
| Job | Two-sided quotes on **cleared** pairs | Find names worth a **Scout** look |
| Vault | `fee_income` rotate only | Research / paper / DARK until a *separate* approval |
| Kill | Code kill on the quote loop | Promotion halt (FLOW kill switches) |
| Output | ENTER / MANAGE / EXIT / SKIP | Candidate + evidence + DARK list |

**Do not mix journals.** A sniper ticket is not an MM `ENTER`. An MM fill is not discovery alpha. Wallet-copy and labeled-flow lanes stay **DARK** without a verified free source ([SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md)). Do not feed discovery PnL stories into the MM Observer brief.

## Next build (CX / Fleet — still fail-closed)

Not a promise that private `main` has these. Gaps stay DARK until wired.

1. **PairProfile** — per-pair spread, size, fee, gas budget, venue, sleeve, DARK list. Quoter reads this; agents write it on the slow loop.
2. **Quoter + skew** — inventory-aware two-sided quotes; skew is code on the fast path, policy on the slow path.
3. **Scout inventory** — which sleeve/venue is actually FREE vs Top-to-add vs DARK. Snapshot: [Scout venue grades (2026-09-09)](#scout-venue-grades-2026-09-09). HYPE **sleeve** stays DARK until the Hyperliquid adapter + mock exists (Scout grade is WARN, not PASS).
4. **Fleet tile** — Ops Ridge cell: sleeve status LIVE|DARK|GAP, kill, fee_income as-of, **no invented PnL %**. See [FLEET-OS.md](./FLEET-OS.md).

## Do not tell Grok / agents

- That @solst1ne (or any viral) PnL is a Helix backtest or live result.
- That HYPE is quotable before a mocked Hyperliquid adapter.
- That Scout PASS is a depth table, a BBO, or a live quote — grades only; full write-up is on the desk box.
- That ETH can ignore gas and run the SOL loop.
- That discovery/sniper tickets belong in the MM JSONL.
- That Risk “usually agrees” with the quoter.
- Secrets, keys, or stub fills when venue / liq / holders / fees / gas are DARK.

Desk truth: [STATUS.md](./STATUS.md). Process rails: [MARKET-MAKER.md](./MARKET-MAKER.md).
