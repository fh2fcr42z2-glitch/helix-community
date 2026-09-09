# Nature of the meme / launchpad market

Process note for Grok and the desk. **Not a buy list. Not a bot. Not Helix PnL.**

Launchpad flow is a **mass-mint machine**. Helix Market Maker is a **fee-vault rotate loop** on names that already clear gates. Do not collapse the two.

## Sources (use vs DARK)

| Source | Use | Do not use as |
| --- | --- | --- |
| **@0xai42exe** (public sector writeup) | Shape of the game: mint rate, rare graduation, wallet-loss base rate, speed vs refusal | Helix backtest, Helix live result, or a sizing formula |
| **Bitquery** Pons / Robinhood Chain vs Solana audit, **4 Aug – 2 Sep 2026** ([investigation](https://bitquery.io/investigations/robinhood-vs-solana-memecoins); [Pons API](https://docs.bitquery.io/docs/blockchain/robinhood/pons-api/)) | Chain comparison: Pons bonding curve (from 12 Aug), Uniswap factories, Pump.fun-class Solana minting, tokenized-equity *quote* assets vs fake-ticker memes | Proof that Robinhood “won,” or a PumpSwap dollar total without noting Bitquery vs DefiLlama basis |
| Viral bot / sniper **PnL** threads | **DARK** | Evidence, journal fields, or “the program works” |

Unverified bot PnL stays **DARK**. Inspiration for *process* (skip, size in code, don’t chase) is allowed. Dollar claims from those posts are not Helix evidence.

Denominators do not mix. @0xai42exe’s ~1.55% graduate figure is **not** the same object as Bitquery’s “curve launches that graduated” among tokens that already hit three traders and $100. Cite the source next to the number. If you cannot, the cell is DARK.

## Sector nature

Mass minting is the product. Survival is not.

| Claim | Order of magnitude | What it means for Helix |
| --- | --- | --- |
| **Mass minting** | ~**200k / month**; peaks near **~20k / day** | Scout cannot “cover the tape.” The default action is **skip**. Inference that tries to read every mint is a cost bug, not research. |
| **Graduation is rare** | ~**1.55%** graduate (source: @0xai42exe; not a Helix count) | Graduation is a liquidity event, not a quality stamp. Most mints never leave the curve. |
| **Fast when they fill** | About **half of grads** fill in ~**4 minutes** | The names that graduate often do it before a human-paced NOTE. Chasing that clock is not an edge. Refusal still is. |
| **Wallet base rate** | ~**2/3 of wallets lose** | A random buy is not a thesis. “Most traders lose” is the background, not a surprise. |
| **Buy-every-mint programs** | Lose **as a group** | Spray-and-pray is a fee for the venue, not a strategy. Helix does not encode “hit every mint.” |
| **Speed ≠ edge** | Latency is table stakes for snipers; it is not alpha for this desk | Faster inference on 20k mints/day still buys noise. MM does not race the first buy. |
| **Refusal = edge** | Skip is the load-bearing skill | Celebrate skips. `fee_income` 0, venue DARK, stale holders → **SKIP / block**. That is the job working. |
| **Tokenized-equity-backed memes** | Pons V2 can quote a launch in native ETH, USDG, or a tokenized stock (TSLA, NVDA, …) | A meme *quoted against* a Robinhood token is not the equity. Fake-ticker memes on Solana (names that look like NVDA / OPENAI) are also not the equity. FLOW still climbs chain → DEX → token. Wallets stay DARK. |
| **Curve vs post-curve** | Pre-grad: bonding-curve contract. Post-grad: AMM / locked pool (PumpSwap-class on SOL; Uniswap v4 + hook on Pons) | Microstructure changes at graduation. LaunchGate (liquidity + holder spread) is a **post-curve** (or already-tradable) check. Curve-snipe is out of MM scope. |

Bitquery window (same 30 days, different filters — do not paste into the table above as if they were the same stats):

- Solana stayed large and flat on top; Robinhood Chain meme volume rose (week 1 → week 4) with almost all of the *curve* growth from **Pons** after **12 Aug 2026**.
- Pons mints along a curve; fill → sweep → locked Uniswap v4 pool. Direct Uniswap factories skip the curve. Flap minted a lot and almost none found a third trader.
- Solana’s crowd is more program-like (top wallets dominate volume; median wallet small). Robinhood’s median wallet was larger in that window. Neither fact is a Helix edge.
- Tokenized stocks *as listed RH tokens* were out of Bitquery’s meme scope. Memes that *pair against* those names are in-scope for Pons quotes. Keep the two stories apart.

**Curve vs post-curve (desk rule):** a bonding-curve print is not a CEX tape and not a graduated pool. Do not average them. If you cannot say which venue the mark came from, the field is DARK.

## Helix maneuvers

How the desk sits in that market. Helix labels only (Sentinel / Sizing / Ops / CoS). No city/heist UI names.

| Maneuver | Rule | Why it fits launchpad nature |
| --- | --- | --- |
| **Skip on errors** | Timeout, 401, 451/403, missing holders, stale liq, kill ON → **SKIP / block**. Never stub a fill or a fee. | 20k mints/day means most paths should fail closed. Retrying into a hole is how spray programs lose. |
| **Size in code** | `size_basis=both` (last_close + depth_cap). Half-Kelly / depth caps live in **config**, not in chat. | “Size it by feel” on a 4-minute grad is sniper cosplay. Code is the only size that journals. |
| **Adversary seat** | Assume other programs are already in the curve. Helix is not the only bot in the room. | Speed-as-identity is their game. Helix’s game is gates + refusal. |
| **Shared box is not a security boundary** | A shared VM, session, or repo checkout is **not** a vault. Keys never live in this community tree. | Launchpad tooling loves “just paste the key.” Helix does not. |
| **Coordinator never signs** | CoS / coordinator **prepares**. Sentinel / Sizing / Ops gate. Signing and live debit stay off the coordinator. Principal vault is read-only. | One front door that can sign becomes a spray program with extra steps. |
| **Celebrate skips** | A skip with a named criterion is a **success**. Log it. Do not “find a mint” to look busy. | Base rate: most mints die; most wallets lose; buy-every-mint loses as a group. Skips are the edge. |
| **Inference cost discipline** | Do not spend model tokens covering the mint firehose. Sample, gate, then stop. | Peak ~20k/day × full NOTE pipeline is not research. It is a bill. FLOW + LaunchGate first; chatter later. |

Kill switch lives in **code**, not in a prompt that says “please stop.” Same doctrine as [MARKET-MAKER.md](./MARKET-MAKER.md) and [CREW-HANDOFF.md](./CREW-HANDOFF.md).

## Fit to Helix pieces

### Market Maker (fee vault)

MM is **LIVE-authorized** (X 2026-09-09) on `fee_income` only; principal locked. LaunchGate: liquidity + holder spread; missing/stale → DARK → block. Enter only if spread is absorbable.

Launchpad nature says the opposite of “rotate every new ticker”:

- New mint ≠ launch. Curve fill ≠ graduated pool. Graduated ≠ liquid enough to exit.
- MM may rotate **after** gates. It does not buy the mint stream.
- `fee_income` 0 or fee source DARK → SKIP is the same maneuver as refusal=edge.

See [MARKET-MAKER.md](./MARKET-MAKER.md). Sleeve map: [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md).

### Crew

Crew gates already match this market: volume before price, liquidity veto, exact invalidation, no chase, social vs on-chain, freshness, size-to-exit, one brief, human go/no-go.

A flying 4-minute grad without the crew is **do not chase**. Wait for the original setup or skip. Unverified crew/bot PnL stays DARK.

See [CREW-HANDOFF.md](./CREW-HANDOFF.md).

### SOL · ETH · HYPE

MM **sleeves** (three books, one process) live in [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md): **SOL** primary · **ETH** try-now · **HYPE** DARK until adapter. This page is launchpad **nature**, not the quote loop. Do not collapse sleeves into a “meme index.”

| Leg | What the launchpad story is | Helix stance |
| --- | --- | --- |
| **SOL** | Industrial bonding-curve mint (Pump.fun-class; Bitquery: ~1.1M Pump.fun tokens in the 30-day window, most never a desk name) | FLOW on free Llama + screener. Wallets DARK. Do not treat PumpSwap dollar prints from one vendor as another vendor’s total. |
| **ETH** | Robinhood Chain (ETH / Arbitrum-tech L2). **Pons** curve → locked Uniswap v4. Quote asset may be ETH, USDG, or a **tokenized stock**. Direct Uniswap factories still mint without a curve. | Tokenized-equity *quote* ≠ listed equity sidecar. Equities remain a future Helix sidecar; this is still a crypto FLOW rung. |
| **HYPE** | Hyperliquid perps are **Top-to-add** — named, not wired, until adapter + mock. Not a launchpad. Meme beta on a perp is not a mint feed. | Field stays **DARK** until Scout catalog + mock say otherwise. Geo/key miss → DARK, no backfill. |

If the NOTE cannot name SOL vs ETH-L2 vs HYPE, the chain rung is DARK. See [FLOW.md](./FLOW.md), [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md), and [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md).

### Five-force lens

Tag the **NOTE**, not “memes.” **DARK if unclear.** Evidence required. [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md).

| Tag | When it might apply here | When it does not |
| --- | --- | --- |
| `force:tech` | Launchpad machinery, curve vs AMM, tokenized-equity *as a quote asset* | “AI coins” as a vibe |
| `force:credit` | Liquidity, fees, vault rules, depth_cap — cited | Easy-money / viral APY |
| `force:internal` | Policy, venue rules, social split **with** tape/search disagreement | Telegram heat alone |
| `force:external` | Chain competition (SOL vs Robinhood Chain) **without inventing wallets** | “War” in a ticker name |
| `force:nature` | Only a cited act of nature | Weather-as-meme |
| `force:DARK` | Default until a claim + source + verification level exists | — |

World Monitor stays DARK without a key. No auto-post.

## Do not tell Grok / agents

- That unverified bot / sniper **PnL** is a Helix backtest or live result.
- That **speed** is Helix’s edge, or that the desk should buy every mint.
- That **~1.55% / ~4 min / ~2/3 lose** were measured by Helix — they are sourced sector shape, not desk telemetry.
- That a **coordinator / CoS signs**, or that a shared box is a key vault.
- That **principal** may be debited, or that venue/liq/holders/fees DARK may be stubbed.
- That **Hyperliquid** is on because this file names it.
- That a meme quoted against **TSLA/NVDA** (or a fake ticker with those letters) is the equity, or that Helix is an equities terminal.
- That **graduation** means safe, investable, or LaunchGate PASS.
- To invent holder counts, whale labels, mint totals, or wallet PnL when the feed is missing.
- Secrets, cookies, wallet seeds, or private helix-cx paths.

Paper-only language for research. MM tickets follow [MARKET-MAKER.md](./MARKET-MAKER.md) rails and [MM-SOL-ETH-HYPE.md](./MM-SOL-ETH-HYPE.md) sleeves only. Not financial advice. Not a broker.
