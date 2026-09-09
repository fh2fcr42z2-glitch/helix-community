# Helix engine flow (anti-clog)

Ideas die in chat. Helix **promotes through files**, one owner at a time, so Grok, Scout, CoS, and Fleet do not clog each other.

This is the **promotion path**, not a live order path. Skip and veto are first-class outcomes. Unknown → **DARK**. No secrets.

Desk truth: [STATUS.md](./STATUS.md). Handoff rules: [CREW-HANDOFF.md](./CREW-HANDOFF.md). Memory layers: [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md).

## Promotion path

```
Idea
  → cowork note
  → Scout INVENTORY flag
  → CoS Cloud Agent PR
  → warehouse / Fleet panel
```

| Stage | Artifact | Owner | Promotes when | Stays put / DARK when |
| --- | --- | --- | --- | --- |
| **Idea** | One sentence + DARK list (chat is fine *only* as a seed) | Whoever noticed it | Written to a cowork note with owner + as-of | Left in a Grok thread, Slack, or “we should…” |
| **Cowork note** | File under cowork `notes/` or `briefs/` (path + decision + source) | Named note owner | Scout can class it or flag INVENTORY | Secrets, helix-cx dumps, or no owner |
| **Scout INVENTORY flag** | Catalog row or flag on [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md) / desk `INVENTORY.md` | Free Market Data Scout | Class is honest (FREE / FREE-TIER / PAID / DARK); Top-to-add ≠ wired | Pretending a named vendor is LIVE; inventing a bar to justify a flag |
| **CoS Cloud Agent PR** | One PR, one job | Chief of Staff (front door) — agent implements | Community **docs** PR *or* **CX PR #1** desk-code change, never both confused as one tree | Agent “just committing to private `main`”; unsupervised merge |
| **Warehouse / Fleet panel** | Quality-gated SQL row and/or Fleet tile | Warehouse / Fleet OS | Real metric + `asOf` + source; tile LIVE or honest DARK | Invented autonomy %, stub fills, DuckDB on by default |

Nothing skips a stage because it felt urgent. A NOTE, MM ticket, or Chart shot still has to walk this path (or an explicit **skip/veto** with a named criterion).

## Rules (anti-clog)

1. **One owner per artifact.** Contributors OK; one named owner. Two “owners” = clog.
2. **Handoffs via files**, not memory. Path + decision + source + as-of. If it only exists in a chat, it has not been handed off.
3. **Grok reads community `main` only.** Auto-pull sees [helix-community `main`](https://github.com/fh2fcr42z2-glitch/helix-community). Do not treat private **helix-cx GitHub `main`** as the live desk. Do not paste private Grok transcripts back into this repo.
4. **CX PR #1 is desk code.** Private [helix-cx PR #1](https://github.com/fh2fcr42z2-glitch/helix-cx/pull/1) is the paper desk + Fleet OS + Chart shots tab. Community PRs are docs/adapters/mocks. Do not ask Grok to “merge the desk” because a community doc landed.
5. **Unknown → DARK.** Missing venue, overlay, wallet, PnL, or panel → DARK / NULL. Never invent to keep the path moving.
6. **Skip and veto are first-class.** A documented SKIP or named veto is a *completed* handoff, not a hole. Do not re-queue a veto without new evidence. Crew: every veto names the failed criterion and the owner to fix it.

Prepare ≠ execute. Live money still needs explicit human approval (MM path: [MARKET-MAKER.md](./MARKET-MAKER.md)). Sentinel still forbids unsupervised orders.

## What each hop is for

**Cowork note** — durable enough for another hat to read tomorrow. Template: owner, claim, evidence URL/as-of, DARK list, next owner. Reader JSON is a cowork-class artifact (FREE ingest map + Alpha handoff on [READER.md](READER.md); desk `helix-cowork` notes may be unmounted). Chart shots use the notes tab + `chart-shots/` **sidecar JSON** (readable card: levels, invalidation, thesis_blurb; five-force spine) — [CHART-BOT.md](./CHART-BOT.md) · [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md). Missing sidecar → DARK metadata. TA learning: `ta-learning/` retros + PATTERN-EDGE-LOG, not silent weights. TA critique pack is desk `helix-cowork` (may be unmounted); community docs are the public contract. Not a Grok paste.

**Scout INVENTORY flag** — classification, not collection of keys. When cowork learns a class, **patch INVENTORY in the same promotion** so catalog and note do not lag. Named ≠ wired.

**CoS Cloud Agent PR** — Chief of Staff is the front door ([CREW-HANDOFF.md](./CREW-HANDOFF.md)). One report, one PR job. Specialist work stays with specialists. Cloud Agent implements; CoS does not become Quant or TA.

**Warehouse / Fleet panel** — queryable fact or a tile bound to a real API/log/file. Fleet: real metrics or DARK — [FLEET-OS.md](./FLEET-OS.md). Warehouse: DuckDB **off-by-default**; DARK > invention — [DATA-AND-MEMORY.md](./DATA-AND-MEMORY.md).

## Fit with other loops

| Loop | Where engine flow sits |
| --- | --- |
| Crew signal path | Gates *inside* a stage (liquidity veto, don’t-chase). Engine flow is how the *artifact* moves between hats. |
| Research loop | Research → code → backtest → (paper) live → post-mortem → fine-tune. Promote code/docs through CoS PR; store failures with `quality_flag`. [RESEARCH-LOOP.md](./RESEARCH-LOOP.md) |
| Alpha Writer NOTE | Scout → Researcher → Market Ops → NOTE. Engine flow is how a NOTE-worthy idea reaches that pipeline without clogging chat. |
| MM / TA | MM journal ≠ Chart shot folder. Separate owners; same promotion discipline. |

## Do not tell Grok / agents

- That private `helix-cx` `main` is the desk (it is a hull; **PR #1** is desk code until Call Me X merges it).
- That a chat idea is INVENTORY.
- That skip/veto means “try again louder.”
- That Fleet tiles may be filled with plausible numbers to look LIVE.
- Secrets, keys, or helix-cx source dumps into community notes.
