# Fleet OS (public)

Grok-readable Fleet / Ops Ridge contract. **Real metrics or DARK — never invent autonomy %.**  
Private CX wiring may lag; use [STATUS.md](./STATUS.md) for LIVE/DARK truth.

---

# Fleet / OS → Helix CX — Cloud Agent refinement brief

**Status:** Phase 1 **kicked** on [helix-cx/pull/1](https://github.com/fh2fcr42z2-glitch/helix-cx/pull/1) (Ops Ridge · specialist cards · Persistent Workspace).  
**This doc:** Phase-1 **metric wiring tips** (for the agent already building) + **Phase 2+** specs (Relationship Graph · Handoff Chord · 5D Lattice · Question pane).  
**Hard rule:** Bind every tile to real APIs/logs/files — else **DARK**. Never invent autonomy %, sync %, or chord arcs.  
**Out of scope:** Live orders · secrets in UI · merge without review · duplicate marketdata adapters.

---

## Role map (keep labels Helix-native)

| Helix role | Artifact / API truth |
|------------|----------------------|
| **Chief of Staff** | PR/CI freshness (`HELIX_FLEET_GITHUB_REPO`), brief handoff count |
| **Scout** | `/workspace/helix-market-data/INVENTORY.md` mtime + optional FREE/PAID/DARK line counts |
| **Cowork Desk** | `/workspace/helix-cowork/QUEUE.md` + `briefs/` file count |
| **Alpha Writer** | `/api/alpha` evidence packet / last compose |
| **Sentinel** | Desk `risk` + KillStrip flags from `/api/quotes` |
| **Quant** (future) | DARK until risk-gates modules land (`brief-risk-gates-wf-dsr-kelly.md`) |
| **Technical Analysis** | `helix-cowork/chart-shots/` mtime + **sidecar JSON** (readable card: levels, invalidation, thesis_blurb; `primary_force` or DARK). Critique PASS as doctrine. First SOL/ETH pack **sketch** (TV guest candles+volume; SuperTrend/%B/RSI/VWAP DARK). Missing sidecar → DARK metadata. Learning: `ta-learning/` files, not weights. CX tab still PR #1 |

Prefer these labels over Klaus/Mara/Cole/Vince unless X asks otherwise.

---

# Part A — Phase 1 wiring tips (Ops Ridge · Fleet row · Workspace)

Phase 1 is already building. Use these **concrete bindings** so metrics stay honest.

### A1. Suggested `/api/fleet` shape (server-only)

```ts
type FleetStatus = "LIVE" | "DARK" | "GAP";

interface FleetCell {
  id: string;
  status: FleetStatus;
  reason?: string;       // required when not LIVE
  asOf?: string;         // ISO
  sources?: string[];    // adapter/file ids
  metrics?: Record<string, number | string | boolean>;
}

interface FleetSnapshot {
  asOf: string;
  ridge: FleetCell[];          // Ops Ridge cards
  specialists: FleetCell[];    // Fleet row
  workspace: Array<{
    path: string;
    kind: "file" | "dir";
    mtime?: string;
    bytes?: number;
    status: FleetStatus;
    reason?: string;
  }>;
  // Phase 1 may omit graph/chord/lattice or stub lattice as DARK
}
```

### A2. Ops Ridge — allowed REAL metrics only

| Card | Wire from | Forbidden |
|------|-----------|-----------|
| **Execution mode** | Constant/`config`: `paper` until explicit live go-ahead; Book rejects `live=true` | Fake “99% autonomous” |
| **Tape freshness** | Max age of BTC (or desk) quote vs now; compare to `HELIX_STALE_MS` | Invented latency histograms without samples |
| **Refresh cadence** | `snap.refreshMs` or `HELIX_TAPE_REFRESH_MS` | — |
| **Rejects (session)** | `GET /api/book` → `rejected.length` (+ optional reason tallies) | Success % without event log |
| **Kill strip flags** | Same fields KillStrip already reads (`risk`, gecko, flow) | Green-washing when any kill is active |
| **In Review** | **DARK** with reason `no PR/brief queue connector` unless you already call GitHub | Placeholder queue counts |
| **Agent task success** | **DARK** until Cloud Agent outcome log exists | Random 90–99% |

Ridge “probability” visual: if you need a bar, use **only** ratios with known denominators, e.g. `liveUniverse / universeSize` from desk rows — label it **“board live share”**, not autonomy.

### A3. Specialist status cards — artifact freshness (not “online”)

| Card | LIVE when | DARK when |
|------|-----------|-----------|
| Scout | `INVENTORY.md` readable; show `mtime` | Path missing / not allowlisted |
| Cowork | `QUEUE.md` readable; show brief file count | Path missing |
| Alpha Writer | Optional: last successful `/api/alpha` in-process cache age | Never composed this process → GAP |
| Sentinel | Desk risk object present | Quotes failed → DARK with HTTP/error |
| CoS | Optional: GitHub PR `#1` state if `gh`/token available | No GitHub → DARK `no repo status` |
| Technical Analysis | `chart-shots/` readable **and** sidecar JSON present; show latest shot as-of | Path missing / no sidecar / no as-of → DARK metadata |

UI copy: **“artifact as-of …”** — never claim agent presence.

### A4. Persistent Workspace — allowlist + redaction

Env (names only):

```
HELIX_FLEET_WORKSPACE_ROOTS=/workspace/helix-market-data,/workspace/helix-cowork
HELIX_FLEET_GITHUB_REPO=fh2fcr42z2-glitch/helix-cx
```

- Resolve paths under allowlist only; reject `..`, `.env*`, `**/secrets/**`, cookies.
- Show: relative path, mtime, bytes (files), child count (dirs).
- PoR dumps under `helix-cowork/proof/por/`: show **file count + total bytes**, never address contents.
- If box paths aren’t mounted in the Cloud Agent VM: return DARK `workspace roots not mounted` — do not invent file lists.

### A5. Phase 1 tests (must stay green)

1. Missing allowlist root → workspace entry DARK + reason.  
2. Quotes failure → Sentinel card DARK; ridge tape freshness DARK/GAP.  
3. No numeric field without a documented source in code comments.  
4. Snapshot JSON includes `asOf`.  
5. `npm test` / `npm run build` green; CX/FLOW/Alpha tabs unchanged.

### A6. IA reminder

```
Tabs: CX | FLOW | Alpha | Fleet OS
CX notes: Chart shots tab (Chart bot; readable card + five-force spine; files under helix-cowork/chart-shots/ + sidecar JSON; first SOL/ETH pack sketch, overlays DARK; learning via ta-learning files; tab still wiring on PR #1)
Fleet OS (phase 1): Ops Ridge | Specialist row | Persistent Workspace
(Defer graph/chord/full lattice/question pane to phase 2+ unless trivial DARK stubs)
```

---

# Part B — Phase 2+ refinements (build next)

## B1. 5D Strategy Lattice (Tape / FLOW / Risk / Alpha / Money-path)

**Sync %** = `(# LIVE sub-signals) / (# declared sub-signals)` per dim — only from enumerated checklist.

| Dim | Sub-signals (examples) | LIVE rule | Else |
|-----|------------------------|-----------|------|
| **Tape** | Coinbase row LIVE, Kraken print, CoinGecko meta | Adapter status LIVE + fresh `asOf` | Geo/HTTP fail → GAP/DARK |
| **FLOW** | DefiLlama leg, DEX Screener, funding/OI/liqs aggregate | At least one verified FLOW leg LIVE | Wallets/bridges stay DARK |
| **Risk** | staleBTC, divergenceBp, dexLiqKill, supertrend | Flags computed from real bars/quotes | WF/DSR/Kelly → DARK until modules exist |
| **Alpha** | evidence packet validates; ≥1 PRIMARY/CROSS/SINGLE fact | `/api/alpha` validate ok | Empty packet → GAP |
| **Money-path** | PoR seed health, OFAC cache, broker checklist | Any gate implemented | Default **DARK** `no live money-path gates yet` |

Cell type:

```ts
{ dim, status, syncPct?: number, subSignals: FleetCell[], asOf?, reason? }
```

Do not show Sync % for Money-path until ≥1 real sub-signal exists.

**Suggested PR:** `feat(ui): Fleet 5D strategy lattice wired to desk/flow/risk/alpha (money-path DARK)`

## B2. Relationship Graph (intent)

**Nodes (fixed topology):** Scout · Cowork · CoS · CX Tape · FLOW · Alpha Writer · Sentinel · (Quant DARK).

**Node health:** map from `/api/fleet` specialists + desk/flow/alpha status.

**Edges light only if both ends LIVE and an observed link exists:**

| Edge | Observed link |
|------|----------------|
| Scout → Cowork | Inventory mtime + cowork notes referencing inventory (optional) |
| Cowork → CoS | `briefs/*.md` count > 0 |
| CoS → CX | PR open/CI (optional GitHub) |
| Tape → Alpha | Alpha evidence `source_ids` intersect tape sources |
| FLOW → Alpha | Same for flow sources |
| Sentinel → Book | Reject reasons referencing kill flags |

No force-directed fluff with random weights. Edge weight = handoff count or `1` if linked.

**Suggested PR:** `feat(ui): Fleet relationship graph with LIVE/DARK nodes (no fake edges)`

## B3. Handoff Chord

**Phase 2a (filesystem + GitHub only):**

| Arc | Source event |
|-----|--------------|
| Cowork → CoS | Brief file created/updated under `briefs/` (mtime) |
| CoS → Cloud Agent | PR commits on `helix-cx` (if GitHub available) |
| Scout → Inventory | Inventory file mtime (self-loop or Scout→desk) |

**Phase 2b (optional event bus):** append-only `data/helix_handoff_events.jsonl` (gitignored or fixtures in tests):

```json
{"ts":"ISO","from":"cowork","to":"cos","kind":"brief","ref":"brief-01-por-ofac.md"}
```

UI draws chords **only** for events in window (e.g. 24h). Empty window → empty chord + label `no handoffs observed`, not decorative arcs.

**Suggested PR:** `feat(ui): Fleet handoff chord from briefs/PRs (optional JSONL later)`

## B4. Question pane (“answer with live data”)

Goal: desk answers more questions **without inventing**.

1. Input: natural-language question.  
2. Router (deterministic first): keyword → panels (`tape`, `flow`, `risk`, `alpha`, `fleet`, `inventory`).  
3. Answer body = **cited fields** from last `FleetSnapshot` + desk/flow/alpha JSON.  
4. Every number carries `source_id` + `asOf`. Missing → explicit **DARK/DATA GAP** sentence.  
5. Reuse Alpha Writer evidence patterns (`claim_type`, `verification`) where useful — **no auto-post**.  
6. LLM optional later for prose only over already-fetched JSON; must not introduce new numerics.

Acceptance: ask “What’s BTC stale status?” → quotes risk fields; ask “Whale labels?” → DARK labeled-flow reason.

**Suggested PR:** `feat(ui): Fleet question pane citing live snapshots (DARK-honest)`

## B5. Phase 4 (after risk-gates + PoR briefs)

- Risk lattice: walk-forward / DSR / `HELIX_KELLY_FRACTION` from `brief-risk-gates-wf-dsr-kelly.md`.  
- Money-path: PoR/OFAC seed health from `brief-01-por-ofac.md`.  
- Still: **no unsupervised live orders** from Fleet UI.

---

# Part C — CoS reply checklist (paste to Cloud Agent)

1. Phase 1: Ops Ridge + specialist cards + Workspace only — **real metrics**; DARK with reasons.  
2. Label freshness as artifact as-of, not online.  
3. Allowlist workspace roots; never render secrets/PoR addresses.  
4. Do not invent autonomy %.  
5. After phase 1 green: lattice → graph → chord → question pane per Part B.  
6. Keep CX/FLOW/Alpha tabs; Fleet OS is additive.  
7. Do not merge until review.

---

## Related Cowork artifacts

| Path | Use |
|------|-----|
| `/workspace/helix-cowork/briefs/brief-risk-gates-wf-dsr-kelly.md` | Phase 4 Risk dim |
| `/workspace/helix-cowork/briefs/brief-01-por-ofac.md` | Money-path / labeled-flow |
| `/workspace/helix-cowork/QUEUE.md` | Cowork card freshness |
| `/workspace/helix-market-data/INVENTORY.md` | Scout card freshness |

**Hand to Chief of Staff** to relay refinements to the Cloud Agent on PR #1.
