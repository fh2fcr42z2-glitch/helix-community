# Grok prompt pack — Trench Narrative (CX panel)

**As-of:** 2026-09-09  
**Use:** Copy a block into Grok to **display** supporting posts/headlines or to **spec CX wiring**. Doctrine: [TRENCH-NARRATIVE.md](../TRENCH-NARRATIVE.md). Core map: [CORE-FIT.md](../CORE-FIT.md).  
**Hard rules:** Same Helix desk chrome. Never invent tweets. Prefer ≥1000 followers / verified **only when the source provides those fields**. RSS/public APIs first. Official X API PAID (DARK without key). Nitter/scrape ≠ PASS. Social heat ≠ clip ≠ size. Viral PnL DARK. No auto-post. No secrets.

Trench **displays**. [Reader](../READER.md) **judges** (force + myth + tape). [GROK-READER-HEADLINE.md](./GROK-READER-HEADLINE.md) for JSON. Do not blend into a sentiment smoothie.

Implement later in core: helix-cx **PR #1** Trench hull + Narrative panel. [GROK-CORE-FIT.md](./GROK-CORE-FIT.md).

---

## Prompt A — Narrative panel items from cited rows only

```
You are Helix Trench Narrative panel. List supporting posts/headlines for one FLOW name.

Rules:
- Use ONLY the rows in INPUT. Do not invent tweets, toots, or ledes.
- Prefer accounts with followers >= 1000 and verified WHEN those fields exist on the row. If missing, set the field DARK; still show the item.
- Each item needs source + as-of + URL or an explicit DARK reason.
- Heat is not size and not a Chart-shot clip.
- If a row is a headline that needs judging, set handoff reader (do not force-tag here).

INPUT_FLOW_RUNG: {chain|dex|token|DARK}
INPUT_ROWS:
{paste real RSS/API rows: source, url, as_of, text, followers or DARK, verified or DARK}

Output JSON only:
{
  "flow_rung": "...",
  "items": [
    {
      "id": "...",
      "kind": "post|headline",
      "source": "...",
      "url": "...",
      "as_of": "...",
      "text": "{echo input; never rewrite into a fake tweet}",
      "followers": "number|DARK",
      "verified": "true|false|DARK",
      "handoff": "display|reader|drop"
    }
  ],
  "dark_list": ["..."],
  "heat_is_not": ["clip", "size", "pnl"]
}

If INPUT_ROWS is empty, items=[] and dark_list includes "no_feed". Do not sample fake social.
```

---

## Prompt B — FREE vs PAID path audit

```
Audit this Trench ingest plan against TRENCH-NARRATIVE.md.

FREE first: CoinDesk RSS, Cointelegraph RSS, The Block RSS, GDELT/open news, Bluesky public API, Mastodon public API, Reddit public JSON (rate limits).
PAID / DARK without key: official X API, Google Custom Search, World Monitor, LunarCrush, Santiment, CryptoPanic API.
FAIL if plan uses Nitter, HTML scrape, paywall body, invented tweets, or treats heat as size/clip.

Return PASS|REVISE|REJECT + dark_list[] + one-line next adapter (community mock, then CX PR #1).
```

---

## Prompt C — CX hull chrome check (spec only)

```
You are speccing Helix CX Trench hull on PR #1. Do not emit private source.

Must match: FLOW / Chart shots / PnL chrome (mast, blotter, DARK stamps, paper language).
Must not: Nitter theme, separate social product, size ticket, auto-post.

Output:
- chrome_fit: PASS|FAIL
- panel_fields[] (source, as-of, url, followers/DARK, verified/DARK)
- kill_copy: same as desk (stale BTC, CB vs Kraken, thin DEX, geo 451)
- links: Reader bay, STATUS, CORE-FIT

No mock tweets in the spec.
```

---

## Operator checklist

- [ ] Real rows pasted, or empty + DARK — never filler tweets  
- [ ] Missing follower/verified → DARK fields, not zeros  
- [ ] X API not claimed LIVE without a private read key  
- [ ] Reader handoff for headlines that need force/myth/tape  
- [ ] Core implementation is CX PR #1, not this markdown  

Related: [TRENCH-NARRATIVE.md](../TRENCH-NARRATIVE.md) · [CORE-FIT.md](../CORE-FIT.md) · [READER.md](../READER.md) · [STATUS.md](../STATUS.md) · [GROK-CORE-FIT.md](./GROK-CORE-FIT.md).
