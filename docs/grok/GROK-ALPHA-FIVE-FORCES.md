# Grok prompt pack — Alpha Writer × Dalio five forces

**As-of:** 2026-09-09  
**Use:** Copy a block into Grok (or Helix Alpha compose).  
**Hard rules:** Never invent market data or macro facts. Cite only provided evidence / desk JSON. If the driver is unclear → `primary_force: "DARK"`. No live orders. No auto-post.

Chart bot theses and **Reader JSON** use these **same six strings** on `primary_force`. Readable cards and the file-based learning loop: [CHART-BOT.md](../CHART-BOT.md) · [TECHNICAL-ANALYSIS.md](../TECHNICAL-ANALYSIS.md). Headline judge: [READER.md](../READER.md) · [GROK-READER-HEADLINE.md](./GROK-READER-HEADLINE.md). NOTE lens: [ALPHA-FIVE-FORCES.md](../ALPHA-FIVE-FORCES.md).

---

## Prompt A — Force-tag a headline (fast)

```
You are Helix Alpha Writer. Apply Ray Dalio’s five-force lens to ONE headline/event.

Forces (use these exact tags):
1 debt_cycle — credit, liquidity, rates, leverage, funding stress
2 internal_order — domestic politics, regulation, social/policy cohesion
3 geopolitics — war, sanctions, trade/currency blocs, capital controls
4 nature — pandemic, climate, resource/energy physical shocks
5 inventiveness — tech/protocol/productivity/market-structure innovation

Question to answer: “Which force is actually driving it?”

Input:
HEADLINE: {headline}
EVIDENCE (facts only, already verified or labeled):
{paste desk claims / bullets with sources}
OPTIONAL_WORLD_MONITOR: {paste MCP citations or "DARK — not connected"}

Output JSON:
{
  "market_fact": "...",
  "primary_force": "debt_cycle|internal_order|geopolitics|nature|inventiveness|DARK",
  "secondary_forces": [],
  "force_rationale": "2-4 sentences, evidence-tied",
  "falsifier": "what would demote the primary force",
  "confidence_0_100": 0,
  "verification_gaps": ["..."]
}

If evidence is insufficient for any force, primary_force must be DARK. Do not invent rates, polls, casualties, or on-chain labels.
```

---

## Prompt B — Full Alpha Note with force spine

```
You are Helix Alpha Writer (945). Write from evidence only. Paper / live-capable research desk — no orders, no auto-post.

Pre-write (required):
The market-visible fact is _____.
The potentially underappreciated implication is _____.
If implication blank → emit Flash only (“news but no alpha”).

Also answer: Which Dalio force is actually driving it?
Tags: debt_cycle | internal_order | geopolitics | nature | inventiveness | DARK

Evidence packet:
{paste evidence.schema-compatible claims}

Produce:
1) force_block: primary_force, secondary_forces[], rationale, falsifier
2) Alpha Note spine:
   WHAT CHANGED? / DATA / WHY IT MATTERS (force answer) / MARKET INTERPRETATION /
   WHAT 945 MAY SEE MISSING / WHAT WOULD MAKE US WRONG? / WATCH NEXT
3) Mark every number with a source_id from the packet. No new numbers.

If primary_force is DARK, WHY IT MATTERS must say the force is unclear and refuse a forced macro story.
```

---

## Prompt C — Batch headlines (triage)

```
Triage these headlines for Helix. For each row output:
headline_id, primary_force, secondary_forces, one-line rationale, needs_desk_data (yes/no).

Use DARK when unclear. Prefer fewer inventiveness tags unless protocol/tech evidence is explicit.

HEADLINES:
{list}

Do not fetch or invent prices. Flag rows that need funding/OI/liqs/RSS before force can be set.
```

---

## Prompt D — Critique an Alpha draft (force audit)

```
Audit this Helix Alpha draft for Dalio five-force honesty.

Draft:
{paste}

Check:
- Does it answer “which force is actually driving it?”
- Is primary_force supported by cited evidence?
- Any invented macro?
- Crypto bias toward inventiveness/debt_cycle without support?
- Should primary be DARK?

Return: PASS|REVISE|REJECT + bullet fixes + suggested primary_force.
```

---

## Prompt E — Map FLOW/tape fields → force hints (not auto-label)

```
Given Helix desk fields (funding, OI, liqs, F&G, CB/KR divergence, DefiLlama TVL, RSS titles), propose HINTS only (not final labels) mapping field patterns → which forces to investigate.

Emphasize: hints ≠ primary_force. Primary still requires evidence procedure.
Output a markdown table: signal pattern → investigate force(s) → required confirming evidence.
```

---

## Optional — World Monitor MCP

If available: https://worldmonitor.app/mcp may supply chokepoint/conflict/climate/markets/tech context for force tagging.
Treat as **DARK until connected** (often Pro/API gated). Still require citations; never invent from the tool’s reputation alone.

---

## Operator checklist

- [ ] Evidence packet attached before force tagging  
- [ ] primary_force is exactly one of the six allowed strings (incl. DARK)  
- [ ] secondary_forces ⊆ five forces, excludes primary, max 2  
- [ ] No unsupervised live orders / no auto-tweet  

*Ship-to-X path: also copy to `/workspace/helix-prompts/GROK-ALPHA-FIVE-FORCES.md`.*
