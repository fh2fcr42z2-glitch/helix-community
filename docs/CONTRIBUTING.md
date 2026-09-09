---
layout: default
title: Contribute
permalink: /contribute/
nav: contribute
---

# Contributing to Helix Community

This is the **public** Helix repo. You are helping other researchers see the desk clearly — docs, interfaces, mocks, and paper ideas. You are not merging into the [private implementation](https://github.com/fh2fcr42z2-glitch/helix-cx).

**Paper-only. Not a broker. Not financial advice. No secrets in issues or PRs.**

If you only read one other file, read [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

The same guide lives at the repository root as `CONTRIBUTING.md` (GitHub’s contributing entry point).

## What we want

| Contribution | Good | Reject |
| --- | --- | --- |
| **Adapter** | One vendor, one port, DARK when unkeyed, tests with mocks | Kitchen-sink client, live key in CI, silent fake bars |
| **Test** | Fixtures + DARK/timeout cases | Recorded HAR files with cookies |
| **Docs** | Corrects a claim, marks DARK, adds a worked paper example | Vendor tutorial that is really a key drop |
| **Paper idea** | Three legs + FLOW rung + invalidation + DARK list | “Buy this,” live sizing, guaranteed edge, auto-post |
| **Interface RFC** | Short, named port, how mocks work | Rewrite the private tree |

Architecture names live in [ARCHITECTURE.md](ARCHITECTURE.md). FLOW and NOTE: [FLOW.md](FLOW.md), [ALPHA-WRITER.md](ALPHA-WRITER.md). Use them even if you dislike the metaphors — the community needs a shared floor plan.

## How to propose an adapter

1. **Open an issue** with the Adapter template (or a short issue titled `adapter: <vendor> → <port>`).
2. State the **port**: `Tape`, `SearchInterest`, `Chatter`, `ChainFlow`, `DexVolume`, `TokenBoard`, or a gated read-only port (`WalletIdentity`, `CexFlow`, `EquitySip`, `OptionsFlow`). There is no community `Swap` / `CreateOrder` port.
3. State the **vendor** and whether it is free or optional/paid.
4. State **DARK behavior** when the key is missing, the pair is missing, or the vendor 429s.
5. Wait for a maintainer or another contributor to say the port shape is right — then PR.
6. In the PR: adapter + mock fixtures + a README paragraph. No live calls required to merge.

Do not implement five vendors in one PR. Do not add a live order, swap, or auto-post method “for completeness.”

## How to open issues

Use a template when you can:

- **Adapter** — a feed behind a port
- **Paper idea** — a social-arbitrage thesis, paper-only
- **Docs** — wrong, missing, or over-claimed

Search open issues first. If you are marking something DARK, say what we currently imply that we should not.

**Never paste secrets**, session cookies, wallet seeds, or screenshots of vendor dashboards that show keys. If the bug is “auth failed,” write `401` and the adapter name.

## PR hygiene

- **Small.** One adapter, one doc fix, one interface tweak.
- **Named after the change**, not after the vibe: `Add CoinGecko tape mock for missing pair`.
- **Tests without network.** If a test needs the internet, it is not a default test.
- **No generated market data as the happy path.** Synthetics must be typed as synthetic and not the default tape ([roadmap](ROADMAP.md)).
- **No secrets.** Run `git diff` with your eyes. If a value looks like a token, it is.
- **Language.** Clear, specific. Not “unlock alpha.”
- **License.** You contribute under MIT.

A maintainer may ask you to split a PR. That is success, not a brush-off.

### Checklist (copy into the PR)

- [ ] No keys, cookies, or `.env` values in the diff
- [ ] Mocks or fixtures; CI does not need my laptop
- [ ] DARK / empty / timeout behavior is explicit
- [ ] Docs updated if I changed a capability claim
- [ ] Paper-only language; no live-trading encouragement
- [ ] No swap, trading, X, or WordPress credentials (not even placeholders-with-values)
- [ ] I did not copy files out of helix-cx

## Local secrets

If you run an adapter against a real vendor on your machine:

```text
cp .env.example .env   # names only
# edit .env locally — never commit it
```

`.env` must be gitignored. `.env.example` lists variable **names**, not values. See [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

## Preview the docs site

GitHub renders the markdown as-is. The Pages site (custom layout in `docs/`) needs Jekyll:

```bash
# from repo root, if you have Ruby/Jekyll
cd docs && jekyll serve --baseurl /helix-community
```

Then open `/helix-community/` on the port Jekyll prints. Do not put keys in that environment.

## Code of conduct

Be kind, be specific, do not harass, do not dump secrets, do not present Helix as a broker. Full text: [CODE_OF_CONDUCT.md](https://github.com/fh2fcr42z2-glitch/helix-community/blob/main/CODE_OF_CONDUCT.md).

## Security

Leaked credentials: [SECURITY.md](https://github.com/fh2fcr42z2-glitch/helix-community/blob/main/SECURITY.md). Do not open a public issue that contains the secret.
