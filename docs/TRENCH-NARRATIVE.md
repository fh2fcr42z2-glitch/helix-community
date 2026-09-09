# Trench Narrative

Public contract for the **Trench** hull and **Narrative** panel. Private wiring lives on helix-cx **PR #1**. This repo documents the rules — not the client.

Trench is the desk’s **chatter / headline** surface for a named FLOW rung. It is not a Twitter clone, not a scrape farm, and not a size ticket. Headlines that need a force tag, myth filter, and tape check hand off to **Reader** — [READER.md](./READER.md) — then Alpha Writer. Trench **displays**; Reader **judges**.

**Social heat ≠ clip. Social heat ≠ size.** Unknown → **DARK**. Never invent tweets. No secrets.

## Hull chrome

Trench sits **inside** the main Helix desk. The hull must match the rest of CX:

| Must match | Must not become |
|---|---|
| Same desk chrome as FLOW / Chart shots / PnL (mast, blotter, DARK stamps, paper language) | A third-party social skin, Nitter theme, or “terminal Twitter” |
| Same hats and kill-switch copy as the rest of the floor | A feed that can place, size, or auto-post |
| Same DARK > fake honesty | A heat map that looks like a clip or a filled book |

If the panel cannot reuse Helix chrome, it is not ready. Wiring stays on helix-cx PR #1 until Call Me X merges it. Do not copy private CX into this repo.

## Narrative panel

The panel shows **supporting posts and headlines** for the name on the desk — evidence for the chatter / search legs, not a blended sentiment score. Do not invent tweets or ledes. Promotion toward a NOTE goes through Reader JSON, not a heat count.

| Prefers | When the source does **not** provide the field |
|---|---|
| Accounts with **≥ 1000 followers** | Do not invent a count. Follower field is **DARK**; the item may still list with honest missing metadata |
| **Verified** accounts | Do not invent a badge. Verified field is **DARK** |

Prefer high-follower and verified **when those fields exist**. A verified 200-follower account is still weaker than an unverified 50k account **if** both counts are real. Missing fields are not zeros.

Every item needs **source + as-of + URL** (or an explicit DARK reason). No date/link → DARK. Paid promo, copied headlines, and bot swarms are noise to filter, not size.

Crew lane: Alpha / Social compares mentions to **on-chain volume** — [CREW-HANDOFF.md](./CREW-HANDOFF.md). Tape still leads. Chatter does not size MM or a Chart-shot clip. If the lede conflicts with the print, Reader believes the tape — [READER.md](./READER.md).

## Nature sense

Two different “nature” words. Do not collapse them. Social heat is neither.

| Sense | What it is | What it is not |
|---|---|---|
| **Dalio `force:nature`** | A cited act of nature on a NOTE (disaster, pandemic, climate shock) — [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md) | Weather-as-meme, “the timeline feels chaotic,” or a vibe tag |
| **Meme-market nature** | Launchpad mass-mint; **skip-as-edge**; bot PnL DARK — [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md) | A reason to clip every viral ticker |
| **Social heat** | How loud public posts/headlines are (this panel) | A **clip** (Chart shot / setup), an MM **size**, a fill, or Helix PnL |

`force:nature` stays **DARK if unclear**; evidence required. World Monitor stays DARK without a key.

Launchpad nature says refusal is the load-bearing skill. A loud Trench does not override skip / LaunchGate / kill switches. Viral mint chatter is still 20k-a-day noise until FLOW and gates say otherwise.

**Social heat ≠ clip:** a trending thread is not a Chart shot, not `setup_grade`, not invalidation. [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md).

**Social heat ≠ size:** mention count is not `size_basis`, not Kelly, not `fee_income`. [MARKET-MAKER.md](./MARKET-MAKER.md), [PNL.md](./PNL.md).

## FREE paths (RSS / public APIs first)

Keyless, within vendor terms and **rate limits**. Cite the feed. Do not scrape a paywall. Named ≠ wired until an adapter + mock exists — [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md).

| Source | Class | Honest note |
|---|---|---|
| **CoinDesk RSS** | **FREE** public headlines | News, not a paid newswire. Not wallet flow |
| **Cointelegraph (CT) RSS** | **FREE** public headlines | Same. Do not treat a headline as tape |
| **The Block RSS** | **FREE** public headlines | Same. Paywall body stays unread / DARK |
| **GDELT / open news** | **FREE** public news graph (typical) | Coarse, multilingual, easy to overfit. Not a tweet |
| **Bluesky public API** | **FREE** public posts (typical) | Prefer ≥1000 followers / verified **when the API returns those fields** |
| **Mastodon public API** | **FREE** public posts (typical) | Instance-local; rate-limit; no invented toots |
| **Reddit public JSON** | **FREE** with **rate limits** | Subreddit heat ≠ size. Respect Reddit’s public JSON rules; 429 → DARK, do not scrape HTML |

**RSS free first.** Google Trends remains the free **search-interest** leg ([CONCEPT.md](./CONCEPT.md)); it is not this panel’s firehose.

Timeout, 401, 429, 451/403 → **DARK** + reason. Do not backfill from a paid vendor or a remembered tweet.

## PAID / DARK without a key

Useful volume and vendor firehoses stay **DARK** on the public bench until a **read-only** research key exists in a *private* environment **and** an adapter + mock exists.

| Source | Class | Honest note |
|---|---|---|
| **Official X API** | **PAID** — useful **volume** | The scale path for X. Unkeyed = **DARK**. Not Nitter. Not auto-post |
| **Google Custom Search** | **PAID** | Search beyond Trends. Unkeyed = **DARK**. CSE is not a free Trends substitute |
| **World Monitor** | **PAID / Pro** MCP or API | Five-force evidence substrate, future/optional. **DARK without a key.** Never paste MCP tokens |
| **LunarCrush** | **PAID** | Social/asset heat vendor. Unkeyed = **DARK**. Heat still ≠ clip or size |
| **Santiment** | **PAID** | Social/on-chain research vendor. Unkeyed = **DARK**. Not a wallet label unlock |
| **CryptoPanic API** | **PAID** | Headlines API. Public HTML/RSS-class pages are not this keyed API |

X **auto-post** stays **DARK / off** even if a read key exists. Read ≠ publish. [ALPHA-WRITER.md](./ALPHA-WRITER.md).

## Hard nos

| Rule | Meaning |
|---|---|
| **No Nitter / scrape as PASS** | Unofficial X mirrors, HTML scrapes, and stolen cookies are **not** a Scout PASS. Official X API is the paid volume path; without it, X is DARK |
| **Viral PnL DARK** | Screenshot threads and bot PnL are not Helix evidence — [PNL.md](./PNL.md), [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md) |
| **Never invent tweets** | No reconstructed posts, no “someone like @x would have said,” no filler heat. Missing feed → empty / DARK |
| **No secrets** | No Bearer tokens, cookies, CSE keys, or MCP tokens in this repo, issues, or screenshots |

A Nitter URL in a cowork note is a research scrap, not a LIVE adapter.

## Env names (if any)

This public file does **not** inventory private helix-cx variable names. If a private `.env` already holds a read-only research key for a PAID row, keep **names only** in local env — **never values**.

Do **not** add X posting tokens, WordPress passwords, or scrape-session cookies to this repo, even blank. Existing `.env.example` already forbids X/publish secrets.

## Do not tell Grok / agents

- That Trench is a different product chrome from the Helix desk.
- That social heat is a Chart-shot **clip**, an MM **size**, or Helix PnL.
- That Nitter, a scrape, or a remembered tweet is a PASS feed.
- That the official X API, Google CSE, World Monitor, LunarCrush, Santiment, or CryptoPanic API is LIVE without a private key + adapter.
- To invent tweets, follower counts, verified badges, viral PnL, or headlines for Reader.
- Secrets, cookies, or private helix-cx paths.

Headlines that need a force tag, myth filter, and tape check: [READER.md](./READER.md).

Paper-only language for research. Not financial advice. Not a broker.
