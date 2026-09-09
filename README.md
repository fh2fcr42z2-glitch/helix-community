# Helix Community

Public docs for Helix — social arbitrage research desk (paper-only).

This repo grows the community: architecture, contribution guide, and what sensitive integrations need (**no secrets**).

Private implementation lives elsewhere. The working desk is a [private repository](https://github.com/fh2fcr42z2-glitch/helix-cx). This public repo does not contain that code, its credentials, or its internal notes. If you cannot open that link, that is expected — treat it as a pointer, not a source tree.

---

Helix studies a specific gap:

**price tape** vs **search interest** vs **social / consumer chatter**.

Those three streams disagree all the time. Sometimes the tape has already moved and search is late. Sometimes people are talking and nobody has bid. Sometimes Google is already asking and the book is quiet. Helix is a research desk for writing those disagreements down, testing them on a **paper book**, and being honest when the data is missing.

It is **not a broker**. It is **not financial advice**. It does not place live orders. Nothing here is an invitation to trade.

**Crypto-first.** The customer experience is built around crypto markets first. Equities are a future sidecar, not the present desk.

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
| [Architecture](docs/ARCHITECTURE.md) | Desk surfaces, data flow, specialist roles (conceptual) |
| [Sensitive integrations](docs/SENSITIVE-INTEGRATIONS.md) | What paid feeds unlock — no credentials |
| [Roadmap](docs/ROADMAP.md) | Public bars, no synthetics, walk-forward, paper-first |
| [Contributing](CONTRIBUTING.md) | Adapters, issues, PR hygiene, secrets rules |
| [Code of conduct](CODE_OF_CONDUCT.md) | Light-touch community rules |
| [Security](SECURITY.md) | How to report a leaked secret |

Rendered site (GitHub Pages): [fh2fcr42z2-glitch.github.io/helix-community](https://fh2fcr42z2-glitch.github.io/helix-community/)

Enable it with **Settings → Pages → Deploy from a branch → `main` → `/docs`**. The site builds from this folder with a small custom layout (no private code, no keys).

## Desk at a glance

Surfaces the community should recognize — names, not private source:

- **Desk** — what is in front of you: candidates, disagreement, next action
- **Process** — thesis → evidence → review → paper book or reject
- **Book** — paper ledger only
- **Risk** — constraints and vetoes on that ledger
- **Fleet / Lab** — future isolated experiments
- **Alpha Writer** — future publish layer for what the desk learned

Roles are conceptual (Head of Desk, Search/Scout, Risk, Sentinel, and others). See [architecture](docs/ARCHITECTURE.md). Sentinel-gated execution stays **paper-first forever** in this community framing.

## What this repo needs

The private build cannot grow a public bench if the only artifacts are closed. This repo is the public bench.

**Highest leverage contributions**

1. **Adapters behind interfaces** — one vendor, one module, mockable.
2. **Tests with mocks** — no live keys in CI.
3. **Docs** — correct a capability claim, mark a feed DARK, write a worked example.
4. **Paper strategy ideas** — a thesis, the three legs (tape / search / chatter), how you would invalidate it.

Do not paste API keys, cookies, wallet seeds, or vendor dashboards into issues or pull requests. Read [sensitive integrations](docs/SENSITIVE-INTEGRATIONS.md) and [CONTRIBUTING.md](CONTRIBUTING.md) first.

## Data honesty

Helix would rather show **DARK** than a plausible fake.

- **Free public APIs** can support a thin, honest desk: Coinbase, Kraken, CoinGecko, DefiLlama, DEX Screener, GeckoTerminal, Google Trends.
- **Wallet identity, smart-money labels, CEX flow, full SIP tape, and options flow** need licenses or keys. Until a key exists *in a private environment*, those capabilities are **DARK**.
- **Synthetic bars are a temporary shame**, not a feature. The public roadmap is to kill them.

A placeholder matrix (what each feed *would* unlock, not what is secretly shipped) lives in [docs/SENSITIVE-INTEGRATIONS.md](docs/SENSITIVE-INTEGRATIONS.md).

## Private implementation

| Public (this repo) | Private |
| --- | --- |
| Docs, contribution process, capability matrix | Application code, configs, runtime |
| Interfaces and mock shapes | Real vendor clients and credentials |
| Paper-method discussion | Any environment that might hold keys |

Link only: [fh2fcr42z2-glitch/helix-cx](https://github.com/fh2fcr42z2-glitch/helix-cx) (private). Do not copy from it into this repo.

## License

Docs and community files are [MIT](LICENSE). Third-party product names belong to their owners. Mentioning a vendor is not a partnership, a redistribution license, or a guarantee that Helix has an account there.
