# Core fit (public contract → helix-cx later)

This page is how **Grok** (and CoS Cloud Agents) take community docs and **later implement them in the private core**.

| Tree | Job |
| --- | --- |
| **helix-community `main`** | Contracts, Scout classes, Grok packs, teaching loop. Auto-pull sees **this** tree. |
| **helix-cx PR #1** | Paper desk + Fleet OS + CX tabs. **Desk code.** Merge only when Call Me X says. |
| **helix-cx GitHub `main`** | Hull / early stub — **not** the live desk |

Community PRs do **not** ship CX. CX PRs do **not** dump source back here. Named ≠ wired. Unknown → **DARK**. No secrets.

Desk truth: [STATUS.md](./STATUS.md). Promotion: [ENGINE-FLOW.md](./ENGINE-FLOW.md). Copy-paste: [GROK-PROMPTS.md](./GROK-PROMPTS.md) · [grok/GROK-CORE-FIT.md](./grok/GROK-CORE-FIT.md).

## How Grok should work

```
STATUS (LIVE/DARK)
  → public contract markdown
  → Grok pack (copy-paste)
  → CoS Cloud Agent PR
       ├─ helix-community: docs / mocks / catalog
       └─ helix-cx PR #1: desk code  ← “fully in the core”
```

1. Read [STATUS.md](./STATUS.md) first. If a row says **wiring on helix-cx PR #1**, the contract is LIVE here and the **client is not in this repo**.
2. Implement against the **public contract**, not a remembered screenshot of CX.
3. Adapters: one vendor, one port, **DARK** on 401 / 429 / 451 / missing key. Mocks in tests. [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md).
4. Teaching ([LEARNING-PATH.md](./LEARNING-PATH.md) · [`teaching/`](../teaching/)) trains honesty. It does not replace CX. Chart bot files stay in [`ta-learning/`](../ta-learning/).
5. When CX wiring lands, **patch STATUS** in the same promotion (honest LIVE vs still DARK). Do not claim core done because a community doc merged.

## Surface map (implement later in core)

Each row is a CX hull piece. **Chrome must match the main Helix desk** (Trench is not a separate social app).

| CX surface (PR #1) | Public contract | Grok pack | Core later (honest) |
| --- | --- | --- | --- |
| **FLOW / Desk** | [FLOW.md](./FLOW.md) · [CONCEPT.md](./CONCEPT.md) | — | Chain → DEX → token; wallets DARK; kill switches halt promotion |
| **Trench hull + Narrative panel** | [TRENCH-NARRATIVE.md](./TRENCH-NARRATIVE.md) | [GROK-TRENCH-NARRATIVE.md](./grok/GROK-TRENCH-NARRATIVE.md) | Same desk chrome; RSS/public APIs first; X API **PAID**; never invent tweets; heat ≠ clip/size |
| **Reader bay** | [READER.md](./READER.md) | [GROK-READER-HEADLINE.md](./grok/GROK-READER-HEADLINE.md) | Cited headline → JSON; tape wins; no fake ledes; no archive.ph |
| **Chart shots tab** | [CHART-BOT.md](./CHART-BOT.md) · [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md) | [GROK-ALPHA-FIVE-FORCES.md](./grok/GROK-ALPHA-FIVE-FORCES.md) | Sidecar JSON; guest pack = `sketch`; no fake charts |
| **Wallet / DEX view** | [WALLET-LOGIN.md](./WALLET-LOGIN.md) | [GROK-CORE-FIT.md](./grok/GROK-CORE-FIT.md) | SIWS/SIWE view-only; Helix never holds keys; HYPE DARK |
| **PnL panel** | [PNL.md](./PNL.md) | [GROK-CORE-FIT.md](./grok/GROK-CORE-FIT.md) | Labeled sources; viral PnL DARK; no fabricated totals |
| **Market Maker** | [MARKET-MAKER.md](./MARKET-MAKER.md) · [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) | [GROK-MARKET-MAKER.md](./grok/GROK-MARKET-MAKER.md) | `fee_income` only; principal locked; skip-as-edge |
| **Fleet OS ridge** | [FLEET-OS.md](./FLEET-OS.md) | [GROK-CREW-HANDOFF.md](./grok/GROK-CREW-HANDOFF.md) | Real metrics or DARK; never invent success % |
| **Warehouse tile** | [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md) | [GROK-SQL-DATASET-PACK.md](./grok/GROK-SQL-DATASET-PACK.md) | DuckDB off-by-default; DARK > invention |
| **PoR / OFAC seeds** | [POR-OFAC-SEEDS.md](./POR-OFAC-SEEDS.md) | [GROK-POR-OFAC-PACK.md](./grok/GROK-POR-OFAC-PACK.md) | Counts only; RPC join DARK |
| **Alpha Writer NOTE** | [ALPHA-WRITER.md](./ALPHA-WRITER.md) · [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md) | [GROK-ALPHA-FIVE-FORCES.md](./grok/GROK-ALPHA-FIVE-FORCES.md) | Evidence-gated; no auto-post |
| **Agent memory** | [AGENTS.md](../AGENTS.md) · [`teaching/`](../teaching/) | [GROK-CORE-FIT.md](./grok/GROK-CORE-FIT.md) | Public-safe bullets + teaching files. **Not** a CX trading tab |

Trench **displays** posts/headlines. Reader **judges**. Writer **publishes a NOTE**. Do not collapse those three in CX.

## Ports (community → core adapters)

Implement behind ports, one vendor per adapter. No `Swap` / `CreateOrder` in community. CX Sentinel stays paper-first.

| Port | Typical FREE first | DARK / PAID until keyed |
| --- | --- | --- |
| `Tape` | Coinbase, Kraken | Binance/Bybit on 451; HYPE until mocked |
| `SearchInterest` | Google Trends | Google Custom Search |
| `Chatter` | RSS (CoinDesk / CT / The Block), Bluesky, Mastodon, Reddit JSON | Official X API, LunarCrush, Santiment, CryptoPanic API |
| `ChainFlow` / `DexVolume` / `TokenBoard` | DefiLlama free, DEX Screener, GeckoTerminal | Bridges, labels |
| Headline ingest | FREE RSS / cited URL | Paywall body, archive.ph (Helix does not ship), Nitter scrape |

Nitter / HTML scrape is **not** a PASS path in core either.

## Done in core (checklist)

A surface is **implemented in core** only when **all** of these are true:

- [ ] Public contract markdown exists on helix-community `main`
- [ ] Grok pack exists (or CORE-FIT row says the pack)
- [ ] helix-cx **PR #1** wires the hull to that contract (same chrome, DARK stamps)
- [ ] Missing feed / key / geo → **DARK** + reason, not a stub number
- [ ] STATUS row updated (wiring vs LIVE vs still DARK)
- [ ] No secrets in either tree’s git

Until then, STATUS stays “wiring on PR #1” or DARK. Teaching PASS ≠ CX LIVE.

## Do not tell Grok / agents

- That helix-community docs **are** the core binary.
- That merging a community PR implements CX.
- That helix-cx `main` is the desk (PR #1 is).
- To copy helix-cx source into this repo, or to invent tweets, bars, PnL, or headlines to look finished.
- Secrets, posting tokens, or archive.ph adapters.
