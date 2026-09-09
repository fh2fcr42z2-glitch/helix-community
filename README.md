# Helix Community

Public docs for Helix — social arbitrage research desk (paper-only).

This repo grows the community: architecture, contribution guide, and what sensitive integrations need (**no secrets**).

Private implementation lives elsewhere. The working desk is a [private repository](https://github.com/fh2fcr42z2-glitch/helix-cx). This public repo does not contain that code, its credentials, or its internal notes. If you cannot open that link, that is expected — treat it as a pointer, not a source tree.

---

Helix studies a specific gap:

**price tape** vs **search interest** vs **social / consumer chatter**.

Those three streams disagree all the time. Sometimes the tape has already moved and search is late. Sometimes people are talking and nobody has bid. Sometimes Google is already asking and the book is quiet. Helix is a research desk for writing those disagreements down, testing them on a **paper book**, and being honest when the data is missing.

It is **not a broker**. It is **not financial advice**. It does not place live orders. Nothing here is an invitation to trade.

**Crypto-first.** The customer experience is built around crypto markets first: **FLOW** (chain → DEX → token, wallets DARK) plus the three social-arbitrage legs, then an evidence-gated **NOTE**. Equities are a future sidecar, not the present desk. Swap and trading connectors stay **off**.

## Stance

| Helix is | Helix is not |
| --- | --- |
| A paper-only research desk | A broker-dealer or exchange |
| Education and method | Financial advice or a signal service |
| Honest about DARK / unknown data | A claim that every feed is wired |
| Crypto-first, equities later | A live equities terminal |
| Community adapters behind interfaces | A dump of private keys or vendor contracts |

If a number did not come from a real bar, a real API, or a labeled mock in a test, it does not belong on the desk. **Invented data is a bug.**

## Read the docs

| Doc | What it covers |
| --- | --- |
| [Social arbitrage](docs/CONCEPT.md) | The gap between tape, Trends/search, and chatter |
| [Architecture](docs/ARCHITECTURE.md) | Desk surfaces, FLOW intake, specialist hats (conceptual) |
| [FLOW](docs/FLOW.md) | Chain → DEX → token → wallets DARK; kill switches |
| [Alpha Writer NOTE](docs/ALPHA-WRITER.md) | Evidence-gated pipeline; no auto-post; WordPress draft-only future |
| [Sensitive integrations](docs/SENSITIVE-INTEGRATIONS.md) | **Living Free Market Data Scout** catalog — FREE in Helix now vs Top-to-add, DARK list, GitHub shells; **no credentials** |
| [Data and memory](docs/DATA-AND-MEMORY.md) | Flexible layers (agent/project memory, INVENTORY, cowork notes, SQL warehouse, Parquet cold); SQL/prompt discipline — DARK>invention, no secrets |
| [Roadmap](docs/ROADMAP.md) | Public bars, no synthetics, walk-forward, paper-first |
| [Contributing](CONTRIBUTING.md) | Adapters, issues, PR hygiene, secrets rules |
| [Code of conduct](CODE_OF_CONDUCT.md) | Light-touch community rules |
| [Security](SECURITY.md) | How to report a leaked secret |

Rendered site (GitHub Pages): [fh2fcr42z2-glitch.github.io/helix-community](https://fh2fcr42z2-glitch.github.io/helix-community/)

Enable it with **Settings → Pages → Deploy from a branch → `main` → `/docs`**. The site builds from this folder with a small custom layout (no private code, no keys).

## Desk at a glance

Surfaces the community should recognize — names, not private source:

- **Desk** — what is in front of you: FLOW rung, disagreement, next action
- **Process** — Scout → Researcher → Market Ops → paper book or reject
- **Book** — paper ledger only
- **Risk** — constraints, vetoes, kill switches (research halts)
- **Fleet / Lab** — future isolated experiments
- **Alpha Writer** — evidence-gated **NOTE**; no auto-post
- **Memory** — agent/project notes, INVENTORY, cowork notes, SQL warehouse, Parquet cold (DARK>invention, no secrets)

Roles are conceptual (Head of Desk, Scout, **Free Market Data Scout**, Researcher, Market Ops, Risk, Sentinel, Alpha Writer). See [architecture](docs/ARCHITECTURE.md), [FLOW](docs/FLOW.md), and the [Scout catalog](docs/SENSITIVE-INTEGRATIONS.md#free-market-data-scout-charter). Sentinel-gated execution stays **paper-first forever**. Swap/trading connectors stay off.

## What this repo needs

The private build cannot grow a public bench if the only artifacts are closed. This repo is the public bench.

**Highest leverage contributions**

1. **Adapters behind interfaces** — one vendor, one module, mockable.
2. **Tests with mocks** — no live keys in CI.
3. **Docs** — correct a capability claim, mark a feed DARK, write a worked example. **Scout catalog** PRs (FREE / FREE-TIER / PAID / DARK) are first-class.
4. **Paper strategy ideas** — a thesis, the three legs (tape / search / chatter), how you would invalidate it.

Do not paste API keys, cookies, wallet seeds, or vendor dashboards into issues or pull requests. Read [sensitive integrations](docs/SENSITIVE-INTEGRATIONS.md) and [CONTRIBUTING.md](CONTRIBUTING.md) first.

## Data honesty

Helix would rather show **DARK** than a plausible fake.

- **Free in Helix now:** Coinbase, Kraken, CoinGecko, DefiLlama free API, DEX Screener, GeckoTerminal, Google Trends.
- **Top-to-add (not wired yet):** Binance/Bybit public (geo may 451/403 → DARK), Deribit public options, Hyperliquid, Fear & Greed, FRED / EDGAR / Alchemy **free tiers** (sidecar/RPC — **not** labels).
- **Not free firehoses:** Unusual Whales — delayed free dashboard; **API is paid + Bearer only**. Theta Data — **no crypto**; equity/options **~1y EOD delayed** FREE-TIER; **intraday/Greeks paid**.
- **Standing DARK:** wallets, bridges, and entity labels without a *verified free* source; CEX entity flow unpaid; X auto-post; WordPress live publish.
- **Synthetic bars are a temporary shame**, not a feature. The public roadmap is to kill them.
- **Read-only research keys** (private env only) may light a gated port. They never go in this repo. Swap/trading connectors remain off.

A living **Free Market Data Scout** catalog (inventory continues) lives in [docs/SENSITIVE-INTEGRATIONS.md](docs/SENSITIVE-INTEGRATIONS.md). Propose adapters with mocks; never paste keys.

## Private implementation

| Public (this repo) | Private |
| --- | --- |
| Docs, contribution process, capability matrix | Application code, configs, runtime |
| Interfaces and mock shapes | Real vendor clients and credentials |
| Paper-method discussion | Any environment that might hold keys |

Link only: [fh2fcr42z2-glitch/helix-cx](https://github.com/fh2fcr42z2-glitch/helix-cx) (private). Do not copy from it into this repo.

## License

Docs and community files are [MIT](LICENSE). Third-party product names belong to their owners. Mentioning a vendor is not a partnership, a redistribution license, or a guarantee that Helix has an account there.
