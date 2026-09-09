---
layout: default
title: About
permalink: /
nav: home
---

# A public bench for a paper desk

<p class="lede">Helix studies the gap between the <strong>price tape</strong>, <strong>Google Trends / search interest</strong>, and <strong>social / consumer chatter</strong>. This site is how contributors grow that desk without touching secrets or the private build.</p>

<ul class="pills">
  <li>Paper-only</li>
  <li>Not a broker</li>
  <li>Not financial advice</li>
  <li>Crypto-first</li>
  <li>Equities later</li>
  <li>DARK &gt; fake</li>
</ul>

## Why a community repo

The working implementation is [private](https://github.com/fh2fcr42z2-glitch/helix-cx). A closed tree cannot recruit adapters, paper theses, or honest docs. **This** repository is the public floor: architecture in plain language, a capability matrix with no keys, and a contribution path that assumes you will never see production credentials.

If you came here to copy a trading bot, stop. If you came here to spec a CoinGecko tape port, mark a feed DARK, or write a three-leg paper idea, stay.

## Social arbitrage, in one pass

The three legs disagree. Helix’s job is to **write the disagreement down**, not to collapse it into a sentiment smoothie.

- Tape: what printed.
- Search: what people queried.
- Chatter: what people said.

A thesis names all three, plus a DARK list for what you could not observe. Full note: [Concept]({{ '/concept/' | relative_url }}).

## Desk map

<div class="grid-cards">
  <article>
    <h2>Desk</h2>
    <p>Attention: candidates, disagreement, next action.</p>
  </article>
  <article>
    <h2>Process</h2>
    <p>Thesis → evidence → review → paper book or reject.</p>
  </article>
  <article>
    <h2>Book</h2>
    <p>Paper ledger only. Hypothetical marks from real bars.</p>
  </article>
  <article>
    <h2>Risk</h2>
    <p>Limits and vetoes on that ledger.</p>
  </article>
  <article>
    <h2>Fleet / Lab</h2>
    <p>Future isolated runs and walk-forward. Still paper.</p>
  </article>
  <article>
    <h2>Alpha Writer</h2>
    <p>Future publish layer: what was learned, not a pick blast.</p>
  </article>
</div>

Roles (Head of Desk, Search/Scout, Sentinel, and the rest) are **conceptual hats**. Sentinel-gated execution stays paper-first **forever** in this community. [Architecture]({{ '/architecture/' | relative_url }}).

## What is gated (and why that helps you)

Wallet identity, smart-money labels, CEX flow, full SIP tape, and options flow sit behind licenses or keys. Until a key exists in a *private* environment, those ports are **DARK**. The free desk still runs on Coinbase, Kraken, CoinGecko, DefiLlama, DEX Screener, GeckoTerminal, and Google Trends.

The matrix — one line per vendor, no credentials — is [Sensitive integrations]({{ '/integrations/' | relative_url }}).

## How to help this week

1. Propose an **adapter** behind a named port, with mocks.
2. Add **tests** that go green without a vendor account.
3. Fix **docs** that over-claim a capability.
4. File a **paper strategy** idea with invalidation and a DARK list.

Rules: [Contribute]({{ '/contribute/' | relative_url }}). North star: [Roadmap]({{ '/roadmap/' | relative_url }}) — real bars, kill synthetics, walk-forward, wallet data only when keyed, Sentinel on.

## Private implementation

[fh2fcr42z2-glitch/helix-cx](https://github.com/fh2fcr42z2-glitch/helix-cx) exists as a private repo. This community does not reproduce its source, configs, or keys. If the link 404s for you, that is the access model working.
