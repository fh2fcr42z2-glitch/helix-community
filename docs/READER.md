---
layout: default
title: Helix Reader
permalink: /reader/
nav: note
---

# Helix Reader

Helix Reader is the **headline judge**, **upstream of Alpha Writer**. It turns a cited public headline into **READER JSON**. It does not publish a NOTE, size a book, or auto-post.

Private wiring (the CX **Reader bay**) lives on helix-cx **PR #1**. This repo is doctrine only.

Paper-only. Not financial advice. Not a broker. **No secrets. No fake headlines. Never invent facts.**

Grok copy-paste: [grok/GROK-READER-HEADLINE.md](grok/GROK-READER-HEADLINE.md). **Grok republish not before 2026-09-14** (credits). This page on community `main` is the live public doctrine now.

Desk Cowork notes (`helix-cowork` Reader doctrine — **may be unmounted**) fold here: **FREE ingest map** + **Alpha handoff rules**. Do not invent the cowork file if the dir is missing. No secrets.

## Where it sits

```
FREE RSS / cited URL
        ↓
headline ingest          (source + as-of + URL, or DARK)
        ↓
Dalio five forces        (same tags as Chart bot / NOTE)
        ↓
rhetoric / myth filter   (lexicon below)
        ↓
tape check               (tape wins vs headline psychology)
        ↓
READER JSON              (handoff: alpha_writer | hold | reject)
        ↓
Alpha Writer NOTE        (evidence-gated; no auto-post)
```

| Surface | Job | Not |
| --- | --- | --- |
| **Trench Narrative** | Show supporting posts/headlines for a named FLOW rung | A size ticket or a NOTE |
| **Reader** | Ingest, force-tag, myth-filter, tape-check → JSON | A publisher, clip, or MM size |
| **Alpha Writer** | Assemble a NOTE when claims are publishable | Auto-post; strip DARK to look sure |

Trench **displays**. Reader **judges**. Writer **publishes**. Chatter does not skip FLOW.

Related: [FLOW.md](FLOW.md) · [TRENCH-NARRATIVE.md](TRENCH-NARRATIVE.md) · [ALPHA-FIVE-FORCES.md](ALPHA-FIVE-FORCES.md) · [ALPHA-WRITER.md](ALPHA-WRITER.md).

## Pipeline

### 1. Headline ingest

**FREE RSS first.** Every ingest row needs **source + as-of + URL** (or an explicit DARK reason). No date/link → DARK. Timeout, 401, 429, 451/403 → **DARK** + reason. Do not backfill from a paid vendor or a remembered headline.

**Never invent a headline.** Missing feed → empty / DARK. Placeholders (`{headline}`) are for Grok packs, not desk rows. Do not reconstruct “what CoinDesk would have said.”

Name a **FLOW rung** (chain / DEX / token) or mark the rung **DARK**. A trending name with no chain and no pair is still a headline, not FLOW. [FLOW.md](FLOW.md).

Display vs judge: Trench **shows** posts/headlines; Reader **ingests** a cited lede. Same vendor list, different job. [TRENCH-NARRATIVE.md](TRENCH-NARRATIVE.md) · [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

## FREE ingest map (Cowork doctrine)

Keyless, within vendor terms and **rate limits**. Cite the feed. Do not scrape a paywall. Named ≠ wired until an adapter + mock exists.

**Reader ingest** = title + link + as-of into JSON. **Alpha cite** uses Writer verification levels ([ALPHA-WRITER.md](ALPHA-WRITER.md)). Paywall **body** is never Observed.

| Source | Class | Reader ingest | Alpha may cite as | Honest note |
| --- | --- | --- | --- | --- |
| **CoinDesk RSS** | **FREE** public headlines | Title + URL + as-of | **Observed** (single feed) | News, not a paid newswire. Not wallet flow. Not tape |
| **Cointelegraph (CT) RSS** | **FREE** public headlines | Title + URL + as-of | **Observed** | Same. Do not treat a headline as a print |
| **The Block RSS** | **FREE** public headlines | Title + URL + as-of | **Observed** (title only) | Paywall body stays unread / **DARK** |
| **GDELT / open news** | **FREE** public news graph (typical) | Title + URL + as-of when the row is real | **Observed** | Coarse, multilingual, easy to overfit. Not a tweet |
| **Cited public page** | **FREE** if the URL is public | Only with URL + as-of | **Observed** | No reconstructed lede. 404/401/429 → DARK |
| **Bluesky public API** | **FREE** public posts (typical) | A **cited** post URL only — not a firehose scrape | **Observed** if URL+as-of exist | Trench display first. Prefer ≥1000 followers / verified **when the API returns those fields**. Do not invent counts |
| **Mastodon public API** | **FREE** public posts (typical) | Cited toot URL only | **Observed** if URL+as-of exist | Instance-local; rate-limit; no invented toots |
| **Reddit public JSON** | **FREE** with **rate limits** | Cited post URL only | **Observed** if URL+as-of exist | Subreddit heat ≠ size. 429 → DARK; do not scrape HTML |
| **Google Trends** | **FREE** search-interest | **No** — not a headline | Search **leg** on the NOTE, not Reader ingest | [CONCEPT.md](CONCEPT.md). Trends is not this map’s firehose |
| **Fear & Greed** | **FREE** public index (typical) | **No** — one number, not a lede | Sentiment context, labeled | Not chatter. Not a headline |

Two independent FREE rows (or tape + headline that actually disagree) may lift a **claim** to **Corroborated**. Stacked copies of the same lede are `consensus_illusion`, not a second source.

### PAID / DARK without a key (not FREE ingest)

Useful volume stays **DARK** on the public bench until a **read-only** research key exists in a *private* environment **and** an adapter + mock exists.

| Source | Class | Reader | Alpha |
| --- | --- | --- | --- |
| **Official X API** | **PAID** — useful **volume** | Unkeyed = **DARK**. Not Nitter. Not auto-post | **Keyed-read** only if the NOTE says it is not free-bench reproducible. Never paste the key |
| **Google Custom Search** | **PAID** | Unkeyed = **DARK**. CSE is not a free Trends substitute | Same keyed-read warning |
| **World Monitor** | **PAID / Pro** MCP or API | **DARK without a key.** Never paste MCP tokens | Force evidence substrate, future/optional — still needs citations |
| **LunarCrush** | **PAID** | Unkeyed = **DARK**. Heat ≠ clip or size | Same |
| **Santiment** | **PAID** | Unkeyed = **DARK**. Not a wallet-label unlock | Same |
| **CryptoPanic API** | **PAID** | Public HTML/RSS-class pages are not this keyed API | Do not upgrade an RSS title to “CryptoPanic API” |

X **auto-post** stays **DARK / off** even if a read key exists. Read ≠ publish.

### Open ingest policy

How a lede is allowed onto the desk. **No automated paywall bypass.**

| Allowed | Not allowed |
| --- | --- |
| **FREE RSS** title + link + as-of | Scraping HTML behind a login or a paywall |
| **Open** public pages (200, no gate) | **archive.ph**, 12ft, outline.com, or any automated “unblock the article” hop |
| **IA-public** — Internet Archive captures of **already-public** pages | Using IA or a mirror to fetch a **paywalled body** the free bench cannot read |
| **User paste** — a human pastes a headline they actually saw, with source + as-of (+ URL if they have one) | Reconstructing a lede from memory, a vibe, or “typical CoinDesk” |

**Paywalled body = DARK.** Title-class RSS is still ingestible. The gated article text is not Observed, not Corroborated, and not a Writer claim until a license-clean open source exists.

**X prefers engine-only archive access for signals** — if a historical **already-public** page is needed, use a Helix engine / **IA-public** path, not a scrape. That preference is **not** a bypass grant. Helix **does not ship** `archive.ph`, 12ft, outline.com, or any paywall-bypass adapter (not this repo, not a Scout PASS, not a LIVE CX ingest). Do not run a bot at archive.ph (or similar) to “complete” Reader JSON. **Paywalled body stays DARK.**

A Nitter URL, a stolen cookie, or a paywall-bypass screenshot in a cowork note is a scrap, not a LIVE adapter.

### Venture-nature packs (pattern)

Reader flags **category_error** when Dalio `nature`, meme-market nature, and social heat get collapsed. Sector **nature packs** teach that split. Same shape as [MEME-MARKET-NATURE.md](MEME-MARKET-NATURE.md): sourced process note, skip-as-edge where it applies, viral PnL DARK, not a buy list.

| Pack | Status |
| --- | --- |
| **Meme / launchpad** | **Done** — [MEME-MARKET-NATURE.md](MEME-MARKET-NATURE.md) |
| **Other crypto ventures** | **Scaffolding** — L2s, RWA, restaking, perps venues, etc. wait for a sourced note. Do not invent a pack to look complete |

A missing venture pack → DARK / omit, not a filler nature story on Reader JSON.

### 2. Dalio five forces

Force tags are **identical** to the NOTE lens and the Chart bot sidecar. Unclear → **DARK**. Never invent rates, wars, polls, disasters, or protocol stories to fill a tag.

| Reader JSON / Chart bot / Grok | NOTE tag | Force (plain language) |
| --- | --- | --- |
| `debt_cycle` | `force:credit` | Money, credit, debt, markets |
| `internal_order` | `force:internal` | Internal order / conflict |
| `geopolitics` | `force:external` | External order / conflict |
| `nature` | `force:nature` | Acts of nature (cited event) |
| `inventiveness` | `force:tech` | Human inventiveness / technology |
| `DARK` | `force:DARK` | Unclear — do not pick a vibe |

`primary_force` is exactly one of those six strings. `secondary_forces` ⊆ the five forces, excludes primary, max 2. Evidence required for every tag. World Monitor stays **DARK without a key**. Full lens: [ALPHA-FIVE-FORCES.md](ALPHA-FIVE-FORCES.md). Chart bot enum: [CHART-BOT.md](CHART-BOT.md) · [grok/GROK-ALPHA-FIVE-FORCES.md](grok/GROK-ALPHA-FIVE-FORCES.md).

Do not collapse **Dalio `nature`** (disaster, pandemic, climate shock) into meme-market nature or “the timeline feels chaotic.” [MEME-MARKET-NATURE.md](MEME-MARKET-NATURE.md) · [TRENCH-NARRATIVE.md](TRENCH-NARRATIVE.md).

### 3. Rhetoric / myth filter

Flag psychology in the copy. Flags are **labels**, not a size, not a clip, not Helix PnL. Unknown → omit the flag (do not invent rhetoric).

| `rhetoric_flags` enum | What it catches | Typical miss |
| --- | --- | --- |
| `appeal_to_authority` | “Expert / whale / insider says” without a cited, dated source | A named public filing or a quoted official with URL + as-of |
| `fear_urgency` | Crash, last chance, act-now — clock without a print | A real kill switch or a dated tape event |
| `scarcity_fomo` | Limited supply / everyone is in / don’t miss it as a reason to size | Measured float, issuance, or pool stats from a free adapter |
| `false_causality` | After this, because of this | Two legs that actually disagree, labeled as disagreement |
| `cherry_pick` | One print or one quote as the whole story | The window, venue, and what was left out |
| `outdated_fact` | Stale as-of sold as now | Honest age; stale snapshot → DARK ([CREW-HANDOFF.md](CREW-HANDOFF.md)) |
| `category_error` | Mixing Dalio nature with meme nature; mixing heat with tape/size/clip | The three nature senses kept apart |
| `viral_pnl_myth` | Screenshot / Discord / bot dollar claims as desk evidence | Viral PnL stays **DARK** — [PNL.md](PNL.md) |
| `loaded_label` | Smart money, whale, manipulation, “they” without a verified free source | Wallets stay DARK without a read-only research key |
| `consensus_illusion` | Stacked copies / “the timeline agrees” as independent corroboration | Two independent public sources, or an honest single-source label |

Paid promo, copied headlines, and bot swarms are noise to flag, not corroboration. Crew lane: Alpha / Social compares mentions to on-chain volume — still not size.

Optional **Niederhoffer theme tags** (`nieder_*`) are curriculum labels, not a sixth force and not evidence — see below. They never override tape or counts.

### 4. Tape check

**Believe the tape over conflicting headline psychology.** Chatter is a leg. It is not a mark.

| Tape vs headline | Reader does |
| --- | --- |
| Headline story **agrees** with a real print (venue + as-of) | `tape_check.status = agrees` — still keep rhetoric flags |
| Headline **FOMO / fear / “whale”** conflicts with the print | **Tape wins.** `status = conflicts`. Psychology stays in `rhetoric_flags`. Do not “fix” the tape to match the lede |
| Tape missing, stale, or a kill switch is on / unmeasured | `status = DARK`. Do not invent a bar so the headline can win or lose |

Kill switches still apply: stale BTC, Coinbase vs Kraken ≥ 25 bp, thin DEX liquidity, geo 451/403. Unmeasured counts as tripped. [FLOW.md](FLOW.md).

**Social heat ≠ size.** Mention count is not `size_basis`, not Kelly, not `fee_income`. **Social heat ≠ clip.** A loud lede is not a Chart shot. [TRENCH-NARRATIVE.md](TRENCH-NARRATIVE.md) · [MARKET-MAKER.md](MARKET-MAKER.md) · [TECHNICAL-ANALYSIS.md](TECHNICAL-ANALYSIS.md).

### 5. READER JSON → Alpha Writer

Output is JSON for the next hat, not a tweet. Schema shape (placeholders only — **no sample news**):

```json
{
  "headline_id": "{id}",
  "source": "{feed or site}",
  "url": "{url or DARK}",
  "as_of": "{timestamp + zone}",
  "headline": "{text as ingested — never invented}",
  "flow_rung": "chain|dex|token|DARK",
  "primary_force": "debt_cycle|internal_order|geopolitics|nature|inventiveness|DARK",
  "secondary_forces": [],
  "force_rationale": "{evidence-tied or DARK}",
  "rhetoric_flags": [],
  "tape_check": {
    "status": "agrees|conflicts|DARK",
    "belief": "tape_wins_when_conflict",
    "evidence_ref": "{bar/venue as-of or DARK}"
  },
  "viral_pnl": "DARK",
  "nieder_tags": [],
  "dark_list": [],
  "handoff": "alpha_writer|hold|reject",
  "handoff_note": "{why}"
}
```

Reader JSON is **intake**, not a substitute NOTE. Handoff enum and Writer gates: **Alpha handoff rules** below. [ALPHA-WRITER.md](ALPHA-WRITER.md).

## Alpha handoff rules (Cowork doctrine)

Reader **owns** the JSON. Writer **owns** the NOTE. One owner per artifact. Handoff is a **file** (path + as-of + JSON), not a chat vibe. [ENGINE-FLOW.md](ENGINE-FLOW.md) · [CREW-HANDOFF.md](CREW-HANDOFF.md).

| Rule | Meaning |
| --- | --- |
| **1. File, not memory** | Next hat gets `headline_id`, source, URL, as-of, JSON path. If it only exists in a Grok thread, it has not been handed off |
| **2. Verification travels** | A single FREE RSS title is **Observed** at most. **Corroborated** needs two independent public sources or two legs that actually disagree. Missing source sold as Observed → **`reject`** |
| **3. Rhetoric ≠ claim** | `rhetoric_flags` label psychology. Writer does not promote a flag into a market fact or a size |
| **4. Themes ≠ evidence** | `nieder_tags` (below) are curriculum labels. They do not fill DARK tape, DARK force, or a missing URL |
| **5. Tape wins on the NOTE** | If `tape_check.status = conflicts`, Writer **keeps tape-wins**. Do not reconcile FOMO/fear into the mark. If tape is DARK, Writer does not invent a bar to finish the NOTE |
| **6. Writer still runs full gates** | FLOW rung, three legs, claims table, kill-switch status, DARK list, paper action, invalidation. Reader JSON does not skip Market Ops |
| **7. `hold` is a completed hop** | Name the missing field (fresh tape, second source, FLOW rung, kill-switch measure). Do not re-queue as `alpha_writer` without that evidence |
| **8. `reject` is a completed hop** | Name the criterion: invented lede/facts, viral PnL as evidence, category error that cannot be stripped, missing source. Do not reopen without new evidence |
| **9. `alpha_writer` is intake only** | Source + as-of + URL exist; force tagged or honest DARK; rhetoric named (or omitted if unsure); tape checked; DARK list present. Writer may still **Blocked** after kill switches / Risk |
| **10. Keyed-read stays a warning** | PAID rows (X API, CSE, World Monitor, …) in a NOTE must say **not reproducible on the free bench**. Never paste the key |
| **11. No auto-post** | Reader does not tweet. Writer does not auto-post. WordPress stays draft-only future |
| **12. Skip / veto first-class** | A named veto (kill switch, Risk, Sentinel) completes the handoff. “Bad headline” is not a veto |

`handoff` enum recap:

| `handoff` | When |
| --- | --- |
| **`alpha_writer`** | Intake complete under rules 2–6 and 9. Writer still runs the full NOTE gates |
| **`hold`** | Rule 7 — named missing desk data |
| **`reject`** | Rule 8 — invented headline or facts; viral PnL offered as evidence; missing source sold as Observed; unstrippable category error |

## Niederhoffer curriculum (themes only)

Helix may tag Reader JSON with **theme labels** drawn from Victor Niederhoffer’s public book **titles** — *The Education of a Speculator* and *Practical Speculation*. **No copyrighted excerpts.** Do not paste chapters, quotes, or tables from those books into this repo, issues, Grok packs, or cowork notes that get promoted here.

Helix learns **themes**, not the books. Tape and **counts** still win. A `nieder_*` tag never overrides a print, a kill switch, or a DARK list.

| `nieder_tags` enum | Theme (plain language) | Must not |
| --- | --- | --- |
| `nieder_ecology` | Markets as roles / niches (who is eating whom), not a single “the market” actor | Invent a food-chain of wallets or labels |
| `nieder_deception` | Headlines and talk can mislead; look for the count that would falsify the story | Treat deception as a whale name or a size |
| `nieder_volume` | Seek volume / participation evidence before a price narrative | Substitute social heat or viral PnL for volume |
| `nieder_base_rate` | Uncounted base rates — what usually happens, with a denominator | Invent a base rate or a win% |
| `nieder_path` | Path traps — the route matters; a lede is not the whole path | Smooth a path with a synthetic bar |

Omit the tag if unsure. **Unknown → no tag**, not a guessed `nieder_*`. These are optional extras on READER JSON. They are not Dalio forces, not `setup_grade`, and not MM `size_basis`.

## Hard nos

| Rule | Meaning |
| --- | --- |
| **No fake headlines** | No reconstructed ledes, no “typical CoinDesk item,” no filler RSS. Missing feed → empty |
| **Never invent facts** | No rates, wallets, wars, PnL, or prints to complete JSON |
| **Viral PnL DARK** | Screenshot threads and bot dollars are not Helix evidence |
| **Social heat ≠ size** | Loud ≠ clip, fill, Kelly, or `fee_income` |
| **Tape over psychology** | Conflicting FOMO/fear does not override a real bar |
| **FREE RSS first** | Do not scrape a paywall; do not treat Nitter / HTML steal as PASS |
| **No paywall bypass** | Helix **does not ship** `archive.ph` / paywall-bypass adapters. X’s engine-only archive preference ≠ a scrape grant. Paywalled body stays **DARK**. User paste of a seen title is not a bypass |
| **No book excerpts** | Niederhoffer **titles** only. No copyrighted chapters, quotes, or tables |
| **No auto-post** | Reader does not tweet. Writer does not auto-post. Read ≠ publish |
| **No secrets** | No Bearer tokens, cookies, CSE keys, or MCP tokens in this repo |

## CX bay (helix-cx PR #1)

The **Reader bay** is desk chrome on the private paper desk — same mast, blotter, DARK stamps, paper language as FLOW / Trench / Chart shots / PnL. Wiring stays on **PR #1** until Call Me X merges it. Do not copy private CX into this repo.

A bay that cannot show DARK, rhetoric flags, and tape-check status is not ready. Empty ingest is honest. Invented rows are a bug.

## Do not tell Grok / agents

- That Reader publishes NOTEs, sizes MM, or auto-posts.
- That social heat is a clip, a size, or Helix PnL.
- That a headline is a tape print.
- To invent headlines, follower counts, wallets, viral PnL, or `nieder_*` tags to fill JSON.
- To paste copyrighted excerpts from *The Education of a Speculator* or *Practical Speculation*.
- That `nieder_*` themes override tape or counts.
- To fetch a paywalled body via **archive.ph** (or similar) so JSON looks complete.
- That X preferring **engine-only** archive access means Helix ships an archive.ph or paywall-bypass adapter. It does **not**. Paywalled body stays DARK.
- To invent a second venture-nature pack because the meme pack exists.
- That World Monitor / X API / CSE is LIVE without a private key + adapter.
- Secrets, cookies, or private helix-cx paths.
- To **republish** the Grok pack **before 2026-09-14**. Community `main` is the live public text **now**; the later Grok pull waits on credits.

Paper-only language for research. Not financial advice. Not a broker.
