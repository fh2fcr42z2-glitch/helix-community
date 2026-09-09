# Grok prompt pack — Core fit (community → helix-cx PR #1)

**As-of:** 2026-09-09  
**Use:** Copy a block into Grok when the job is **later implement in the private core**.  
**Map:** [CORE-FIT.md](../CORE-FIT.md). **Truth:** [STATUS.md](../STATUS.md).  
**Hard rules:** Grok auto-pulls helix-community **`main` only**. Desk code = helix-cx **PR #1** until Call Me X merges. Do not dump CX source here. Unknown → DARK. No secrets. No live orders. No auto-post. Social heat ≠ clip/size. Never invent tweets, bars, PnL, or headlines.

Teaching loop trains honesty ([LEARNING-PATH.md](../LEARNING-PATH.md) · [`teaching/`](../../teaching/)). It does **not** mark a CX tab LIVE.

---

## Prompt A — Pick a surface and implement against the contract

```
You are Helix CoS implementer. Job: wire ONE CX surface on helix-cx PR #1 to the public contract. You are not editing helix-cx from the community tree.

Read first: docs/STATUS.md, then docs/CORE-FIT.md, then the contract row for SURFACE.

SURFACE: {Trench | Reader | Chart shots | Wallet | PnL | MM | Fleet | FLOW | NOTE}

Rules:
- Match main Helix desk chrome. Trench is not a Nitter skin.
- Named ≠ wired. If STATUS says DARK or “wiring on PR #1”, do not claim LIVE.
- Adapters: one vendor, one port. 401/429/451/missing key → DARK + reason. No CoinGecko backfill after a 451.
- RSS/public APIs first for chatter. Official X API is PAID. Nitter/scrape is not PASS.
- Helix does not ship archive.ph. Paywalled body DARK.
- Viral PnL DARK. Heat is not size and not a Chart-shot clip.
- Wallets DARK on FLOW. Connect is SIWS/SIWE view-only if SURFACE is Wallet.
- No Swap/CreateOrder. No X posting tokens.

Output:
1. contract_paths[] (markdown on helix-community main)
2. grok_pack (path or none)
3. cx_surface (what PR #1 must show)
4. dark_list[] (what stays DARK without key/geo/adapter)
5. acceptance[] (checklist from CORE-FIT “Done in core”)
6. community_pr_job (docs/mocks only, or “none — already on main”)
7. cx_pr_job (one sentence for PR #1; do not paste private source)

If you lack the contract, stop and say DARK — do not invent a UI.
```

---

## Prompt B — Gap list (STATUS vs core)

```
You are Helix Scout/CoS. Diff STATUS.md against CORE-FIT.md.

For each CX surface row:
- community_contract: LIVE | missing
- grok_pack: LIVE | missing
- cx_wiring: STATUS wording (quote the cell, do not guess)
- next_owner: community docs | CX PR #1 | human X
- blocker: DARK reason or none

Do not invent Fleet success %. Do not treat teaching PASS as CX LIVE.
No secrets. No helix-cx file paths.
```

---

## Prompt C — Adapter ticket for core (FREE first)

```
Propose ONE adapter Helix CX will need for SURFACE, using the Scout catalog.

Port: Tape | SearchInterest | Chatter | ChainFlow | DexVolume | TokenBoard | (gated read-only only if STATUS allows)
Vendor: {one name}
Class: FREE | FREE-TIER | PAID | DARK
DARK on: 401, 429, 451/403, missing key, missing pair
Mocks: required in tests; CI has no keys
Not: Nitter, paywall scrape, archive.ph, X auto-post

Output a community issue skeleton: title adapter: {vendor} → {port}
Then: what CX PR #1 will call once the mock exists.

Catalog: docs/SENSITIVE-INTEGRATIONS.md
Trench chatter: docs/TRENCH-NARRATIVE.md
```

---

## Operator checklist

- [ ] STATUS read first  
- [ ] Contract markdown + CORE-FIT row named  
- [ ] Community vs CX PR jobs not mixed as one git tree  
- [ ] DARK list explicit  
- [ ] No invented tweets / bars / PnL / headlines  
- [ ] Teaching files unchanged unless the job was a teaching session  

Related: [CORE-FIT.md](../CORE-FIT.md) · [ENGINE-FLOW.md](../ENGINE-FLOW.md) · [TRENCH-NARRATIVE.md](../TRENCH-NARRATIVE.md) · [GROK-TRENCH-NARRATIVE.md](./GROK-TRENCH-NARRATIVE.md) · [GROK-READER-HEADLINE.md](./GROK-READER-HEADLINE.md) · [AGENTS.md](../../AGENTS.md).
