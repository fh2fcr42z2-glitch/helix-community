---
layout: default
title: Data and memory
permalink: /memory/
nav: memory
---

# Data and memory

Helix needs **flexible memory**: what the desk knew last session, what the Scout already classified, what a coworker wrote down, what SQL can prove, and what Parquet can replay. This page is the **public contract** for those layers. It is not a dump of the private warehouse, not a Grok chat export, and not a key vault.

**DARK beats invention. No secrets in any layer.** Paper-only. Not a broker. Not financial advice.

If a number did not come from a real bar, a labeled mock, or an explicit DARK, it does not belong in memory. See [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md) and [FLOW.md](FLOW.md).

## Layers (conceptual)

Hot to cold. Implementations may merge boxes; the **jobs** stay separate.

```
agent memory     ─┐
project memory   ─┤  working / durable notes
INVENTORY        ─┤  Scout catalog (living)
cowork notes     ─┘  human + agent, still no keys
        ↓  only gated facts
SQL warehouse       queryable research (quality gates)
        ↓  only sealed history
Parquet cold        replay / walk-forward
```

| Layer | Question it answers | May hold | Must not hold |
| --- | --- | --- | --- |
| **Agent memory** | What did *this* agent pass just learn? | Ephemeral working context: last FLOW rung, open DARK list, next mock to write | Keys, Bearer tokens, private helix-cx paths, live-order intent |
| **Project memory** | What should the *desk* still know next week? | Durable public-safe facts: ports, kill-switch defaults, “FREE in Helix now” | Secrets, unpublished P&L, Grok transcripts |
| **INVENTORY** | What sources exist, and how are they classed? | Living Scout catalog: FREE / FREE-TIER / PAID / DARK, Top-to-add | Pretending Top-to-add is wired; vendor passwords |
| **Cowork notes** | What did a human and an agent decide together? | Research scraps, NOTE drafts, “we tripped stale BTC” | Pasted `.env`, private chat dumps, wallet seeds |
| **SQL warehouse** | What can we *query* without lying? | Quality-gated facts: venue, timestamp, class, DARK flags. **DuckDB off-by-default** | Invented bars, unlabeled synthetics, connection strings in git, always-on warehouse in CI |
| **Parquet cold** | What can we *replay* later? | Sealed historical files for walk-forward / Lab | Hot secrets, a second silent tape that disagrees with SQL |

**INVENTORY** is the Scout’s living list — the public snapshot is [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md). Memory does not get to override a DARK class because a NOTE sounded better.

**Cowork notes** are how agents and humans leave a trail (Scout findings, egress 451s, “PoR page was 404”). They are not a license to paste Grok threads or helix-cx internals into this repo. When cowork learns a class, **patch INVENTORY in the same PR** so these two docs do not lag.

**SQL warehouse (DuckDB or similar) is off-by-default.** A contributor must opt in locally. Default-off means CI and fresh clones do not silently persist a warehouse. When on: still no secrets, still DARK>invention, still paper-only.

Nothing in this table is a trading venue. Sentinel still forbids live `create_order` and swap paths. Alchemy, if used, is **`eth_call` only**.

## SQL and prompt discipline

Contributors who touch warehouse schemas, ETL, or “ask the model to write SQL” follow the same honesty as adapters.

1. **DARK > invention.** Missing venue, 401, 451/403, unpaid feed, unkeyed UW API, unlabeled wallet → a DARK row or an empty result. Never `COALESCE` a fake print. Never interpolate a hole and call it tape.
2. **No secrets.** No keys in SQL comments, dbt YAML, notebooks, prompt files, or issue text. Warehouse connection strings stay in a private env. This repo lists **names** only (see `.env.example`).
3. **Mocks in tests.** CI queries fixtures, not Coinbase. A walk-forward job that needs the internet is not a default test.
4. **Class travels with the row.** FREE / FREE-TIER / PAID / DARK and a capability category (tape, TVL/DEX, funding/OI, whale/flow, options, sentiment) belong next to the fact. ETL that strips the class is a bug.
5. **Paper marks only.** Warehouse P&L is hypothetical. Parquet fills are not broker fills.

If you are unsure whether a column is a real bar, it is DARK until a Scout catalog row plus an adapter mock say otherwise.

## Grok SQL prompt themes (no prompt dump)

Private Grok (or any model) sessions may exist to help design warehouse SQL. **This community does not publish those prompts, chats, or credentials.** What *is* public is the **theme list** — so contributors aim at the same problems without needing a secret gist.

| Theme | Public intent | Out of bounds |
| --- | --- | --- |
| **Warehouse** | What belongs in SQL vs notes vs Parquet; grain (venue × instrument × time); how DARK is stored as a first-class value | Connection URLs, role passwords, copying helix-cx DDL verbatim |
| **Quality gates** | Freshness (stale BTC), venue disagreement (Coinbase vs Kraken ≥ 25 bp), thin DEX liquidity, **geo egress** (451/403 → DARK), class/DARK checks before a row is queryable | Turning a failed gate into a blended “fair price” |
| **ETL** | Free adapters → stage → warehouse; backoff; DARK on empty/401/451; **`eth_call` only** on Alchemy; never scrape a delayed UW dashboard as if it were the paid API | Embedding Bearer tokens in extract jobs; silent CoinGecko fill after a Binance 403; `eth_send*` |
| **Walk-forward (WF)** | Freeze a question; form it on window A; score on later window B; keep DARK lists on both; Lab/Parquet replay | Look-ahead joins; using the test window to pick the thesis; marketing hypothetical P&L |

When you open an issue like `sql: quality gate for stale BTC`, describe the **theme** and the **gate**. Do not paste a private prompt. Do not paste warehouse output that includes keys.

A contributor-shaped SQL change looks like: contract (columns + DARK behavior) → fixture rows → test that invention cannot pass the gate → docs line here or in [ROADMAP.md](ROADMAP.md). **Do not turn DuckDB on in CI by default.**

## Research risk gates (not live sizing)

These are **Lab / paper-book** gates. They never place an order. They are not financial advice.

| Gate | Research job | Must not |
| --- | --- | --- |
| **WF** (walk-forward) | Thesis formed on window A, scored on later B; DARK list on both | Look-ahead; calling WF “live validated” |
| **DSR** (deflated Sharpe — research statistic) | Discount in-sample Sharpe when many questions were tried | Selling a DSR as a track record |
| **Kelly** (fractional Kelly on the *paper* book) | Hypothetical sizing math so Risk has a number to veto | Live leverage; “the desk is at full Kelly” as a trade rec |

If cowork computes Kelly or DSR, the note must say **research / paper**. SQL may store the *inputs* (returns series with DARK flags). It may not store a secret “optimal live weight.”

Warehouse default: **DuckDB off**. Opt in locally with the env **name** `HELIX_DUCKDB` (see `.env.example`). Absent or empty = off. Off means no warehouse file appears in git or CI artifacts. Never commit the database file.

## GitHub shells (same list as Scout)

When cowork sketches ETL or tape adapters, cite the shells already in [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md) — do not invent a private gist:

- [ccxt/ccxt](https://github.com/ccxt/ccxt) — venue clients; DARK on 451/403
- [nirholas/crypto-data-aggregator](https://github.com/nirholas/crypto-data-aggregator)
- [eliasfire617/crypto-market-data-mcp](https://github.com/eliasfire617/crypto-market-data-mcp)
- [aitrading-bot/nestor](https://github.com/aitrading-bot/nestor) — paper-only patterns here
- [visioneth/AlphaScope](https://github.com/visioneth/AlphaScope)
- [hyperliquid-dex/hyperliquid-python-sdk](https://github.com/hyperliquid-dex/hyperliquid-python-sdk)

Citing ≠ shipping. Check licenses. No keys from their issues.

## What each layer forgets on purpose

- Agent memory **expires**. Do not treat it as the book.
- Project memory **does not** remember secrets “for convenience.”
- INVENTORY **does not** remember a paid feed as FREE because a dashboard loaded.
- Cowork notes **are not** the Alpha Writer NOTE until Process + Market Ops + verification levels say so ([ALPHA-WRITER.md](ALPHA-WRITER.md)).
- SQL **does not** store live orders. There are none here. DuckDB stays **off** until someone opts in.
- Parquet **does not** become the default tape in the Desk UI. Replay is Lab.
- Cowork **does not** leave Scout findings only in chat — INVENTORY / this catalog must move.

## How to help

- Propose warehouse / ETL / gate tests with **mocks**. DuckDB **off-by-default**.
- Keep INVENTORY honest (Scout catalog PRs): PoR/OFAC seeds, news RSS, `eth_call`-only, geo 451/403.
- Record **WF / DSR / Kelly** only as paper research, never as live sizing.
- Add a cowork-note template that has a DARK list, an egress outcome, and a “no secrets” checkbox.
- Never commit Parquet that was built with a real key in the path or metadata.

Same rule as everywhere else: [CONTRIBUTING.md](CONTRIBUTING.md). Leaks: [SECURITY.md](https://github.com/fh2fcr42z2-glitch/helix-community/blob/main/SECURITY.md).
