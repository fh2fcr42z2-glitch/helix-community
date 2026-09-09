# Helix desk learning path

Teaching output (`create-learning-path`) for Grok, Cloud Agents, and public contributors. **Not a buy list. Not a bot. No secrets.**

**Now (2026-09-09):** Phase 2 **PASS**. Next = Phase 3 (NOTE skeleton). File loop: [`teaching/`](../teaching/) · [PROGRESS.md](../teaching/PROGRESS.md).

Baseline: you can read Markdown and GitHub PRs. You have not internalized LIVE vs DARK on this desk.

Target: ship honest public docs (and mocked adapters) that survive [STATUS.md](./STATUS.md) without inventing tape, tweets, or PnL.

Chart bot pattern retros stay in [`ta-learning/`](../ta-learning/) — this path is the **whole floor**, not silent weights.

Upstream skills (vendored, MIT): [continual-learning](https://github.com/cursor/plugins/tree/main/continual-learning) · [teaching](https://github.com/cursor/plugins/tree/main/teaching).

## Materials (small set)

1. [STATUS.md](./STATUS.md) — LIVE / DARK truth (read first, every session)
2. [CONCEPT.md](./CONCEPT.md) + [FLOW.md](./FLOW.md) + [SENSITIVE-INTEGRATIONS.md](./SENSITIVE-INTEGRATIONS.md)
3. [ALPHA-WRITER.md](./ALPHA-WRITER.md) + [ALPHA-FIVE-FORCES.md](./ALPHA-FIVE-FORCES.md)
4. [MARKET-MAKER.md](./MARKET-MAKER.md) + [MEME-MARKET-NATURE.md](./MEME-MARKET-NATURE.md)
5. [TECHNICAL-ANALYSIS.md](./TECHNICAL-ANALYSIS.md) + [CHART-BOT.md](./CHART-BOT.md) + [`ta-learning/`](../ta-learning/)
6. [TRENCH-NARRATIVE.md](./TRENCH-NARRATIVE.md) + [READER.md](./READER.md)
7. [WALLET-LOGIN.md](./WALLET-LOGIN.md) + [PNL.md](./PNL.md)
8. [AGENTS.md](../AGENTS.md) — public-safe bullets only

Do not add a ninth core doc to this list without dropping one.

## Phases

### 1. Honesty floor

**Outcome:** you can explain DARK > invention in one sentence.

**Practice:** open STATUS. Name three LIVE pieces and three DARK pieces. Do not “fill in” a DARK cell.

**Checkpoint:** a note with no invented metric. Fail if you used a viral PnL screenshot as Helix evidence.

**Reflect:** what did you almost invent?

### 2. FLOW + Scout catalog

**Outcome:** climb chain → DEX → token; wallets stay DARK; classify a source as FREE / FREE-TIER / PAID / DARK.

**Practice:** pick one Top-to-add row in the Scout catalog and write DARK behavior for 401 / 429 / 451.

**Checkpoint:** you did not treat a delayed dashboard as a live API.

### 3. NOTE + five forces

**Outcome:** a NOTE needs FLOW, three legs, kill-switch status, DARK list, invalidation. Force tags need evidence; unclear → `force:DARK`.

**Practice:** draft a fictional NOTE skeleton (no live call). Leave World Monitor DARK.

**Checkpoint:** no auto-post. No stripped DARK list.

### 4. Skip-as-edge (MM + meme nature)

**Outcome:** MM is `fee_income` only; principal locked; skip on venue/liq/holders DARK. Launchpad mass-mint is not the fee-vault loop.

**Practice:** write one SKIP with a named criterion. Do not size in chat.

**Checkpoint:** social heat did not become size.

### 5. TA + Chart bot files

**Outcome:** guest candles+volume = `sketch`. Sidecar required. Pins frozen (pivot N=2, VWAP UTC day, BOS alone ≠ confluent).

**Practice:** copy `ta-learning/RETRO.template.md` locally; fill **only** if you have a real resolved claim. Otherwise leave the log empty.

**Checkpoint:** no fabricated PATTERN-EDGE-LOG row. No fake chart.

### 6. Chatter + headlines (Trench + Reader)

**Outcome:** Trench chrome matches the Helix desk. RSS/public APIs first. Reader judges cited headlines → JSON, then Alpha Writer. Never invent tweets or headlines.

**Practice:** list one FREE path and one PAID/DARK-without-key path from TRENCH-NARRATIVE. Mark Nitter as not PASS.

**Checkpoint:** follower/verified fields DARK when the source omits them. Helix does not ship archive.ph.

### 7. Connect + PnL honesty

**Outcome:** SIWS/SIWE is view-only. Cross-source PnL stays labeled separate. Incomplete → badge, not `0`.

**Practice:** say what happens when Coinbase account read is 401.

**Checkpoint:** no Helix-held keys. Viral PnL DARK.

### 8. Ship a public-safe PR, then core later

**Outcome:** one docs (or mocked adapter) PR against community `main`. **Core implementation** is a later helix-cx **PR #1** job against [CORE-FIT.md](./CORE-FIT.md) — not this tree.

**Practice:** contract markdown + STATUS row + README link + Grok pack if the surface is CX. Fetch `origin/main` first.

**Checkpoint:** checklist in `.github/PULL_REQUEST_TEMPLATE.md` is honest. No helix-cx dump. Do not tell Grok the community merge *is* the desk.

Grok copy-paste when implementing CX: [GROK-CORE-FIT.md](./grok/GROK-CORE-FIT.md) · Trench: [GROK-TRENCH-NARRATIVE.md](./grok/GROK-TRENCH-NARRATIVE.md).

## Rubric (use with `run-learning-retrospective`)

| Score | Meaning |
| --- | --- |
| **PASS** | Named DARK list; sources cited; no invented tape/tweets/PnL; STATUS not contradicted |
| **WARN** | Right shape, but collapsed two books, or treated heat as size, or skipped a kill switch |
| **FAIL** | Secrets, scrape-as-PASS, fabricated log row, live-order language, or archive.ph adapter |

After a FAIL, repeat the phase. After a PASS, run `run-learning-retrospective` and adjust pacing — do not add materials.

## What this path will not do

- Calendar-week promises (work in phases; stop when the checkpoint is honest)
- Train Chart bot weights (that is `ta-learning/` files, and the log is empty until real)
- Unlock paid APIs
- Replace STATUS.md
