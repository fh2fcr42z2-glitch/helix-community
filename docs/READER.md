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

Grok copy-paste: [grok/GROK-READER-HEADLINE.md](grok/GROK-READER-HEADLINE.md). A later Grok republish is planned around **2026-09-14** (credits). Docs on this `main` are live now.

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

**FREE RSS first.** Same public-headline class as Trench: CoinDesk / Cointelegraph / The Block RSS, GDELT-class open news, cited public pages. Paywall body stays unread / DARK. Official X API, Google CSE, World Monitor, LunarCrush, Santiment, CryptoPanic API stay **PAID / DARK without a key**. [TRENCH-NARRATIVE.md](TRENCH-NARRATIVE.md) · [SENSITIVE-INTEGRATIONS.md](SENSITIVE-INTEGRATIONS.md).

Every ingest row needs **source + as-of + URL** (or an explicit DARK reason). No date/link → DARK. Timeout, 401, 429, 451/403 → DARK + reason. Do not backfill from a paid vendor or a remembered headline.

**Never invent a headline.** Missing feed → empty / DARK. Placeholders (`{headline}`) are for Grok packs, not desk rows. Do not reconstruct “what CoinDesk would have said.”

Name a **FLOW rung** (chain / DEX / token) or mark the rung **DARK**. A trending name with no chain and no pair is still a headline, not FLOW. [FLOW.md](FLOW.md).

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
  "dark_list": [],
  "handoff": "alpha_writer|hold|reject",
  "handoff_note": "{why}"
}
```

| `handoff` | When |
| --- | --- |
| **`alpha_writer`** | Source + as-of + URL exist; force is tagged or honest DARK; rhetoric flags named; tape checked; DARK list present. Writer still runs the full NOTE gates |
| **`hold`** | Needs desk data (tape freshness, second source, FLOW rung, kill-switch measure) before a NOTE draft |
| **`reject`** | Invented headline or facts; viral PnL offered as evidence; missing source sold as Observed; category error that cannot be stripped |

Alpha Writer still needs FLOW rung, three legs, claims table, kill-switch status, DARK list, paper action, invalidation. Reader JSON is **intake**, not a substitute NOTE. [ALPHA-WRITER.md](ALPHA-WRITER.md).

## Hard nos

| Rule | Meaning |
| --- | --- |
| **No fake headlines** | No reconstructed ledes, no “typical CoinDesk item,” no filler RSS. Missing feed → empty |
| **Never invent facts** | No rates, wallets, wars, PnL, or prints to complete JSON |
| **Viral PnL DARK** | Screenshot threads and bot dollars are not Helix evidence |
| **Social heat ≠ size** | Loud ≠ clip, fill, Kelly, or `fee_income` |
| **Tape over psychology** | Conflicting FOMO/fear does not override a real bar |
| **FREE RSS first** | Do not scrape a paywall; do not treat Nitter / HTML steal as PASS |
| **No auto-post** | Reader does not tweet. Writer does not auto-post. Read ≠ publish |
| **No secrets** | No Bearer tokens, cookies, CSE keys, or MCP tokens in this repo |

## CX bay (helix-cx PR #1)

The **Reader bay** is desk chrome on the private paper desk — same mast, blotter, DARK stamps, paper language as FLOW / Trench / Chart shots / PnL. Wiring stays on **PR #1** until Call Me X merges it. Do not copy private CX into this repo.

A bay that cannot show DARK, rhetoric flags, and tape-check status is not ready. Empty ingest is honest. Invented rows are a bug.

## Do not tell Grok / agents

- That Reader publishes NOTEs, sizes MM, or auto-posts.
- That social heat is a clip, a size, or Helix PnL.
- That a headline is a tape print.
- To invent headlines, follower counts, wallets, or viral PnL to fill JSON.
- That World Monitor / X API / CSE is LIVE without a private key + adapter.
- Secrets, cookies, or private helix-cx paths.
- To wait on a 2026-09-14 Grok republish before using **this** doctrine — community `main` is the live public text.

Paper-only language for research. Not financial advice. Not a broker.
