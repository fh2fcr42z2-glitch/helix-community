# Grok pack — PoR / OFAC address seeds (URLs + tiny samples)

**As-of:** 2026-09-09 (America/Chicago)  
**Audience:** Main Grok / helix-community readers (no box filesystem access)  
**Rule:** Official sources only. Never invent wallet labels. Full dumps stay on operator box under `helix-cowork/proof/por/` — **not** in this pack.

Helix pattern: **official PoR/OFAC seeds ⨝ raw transfers (RPC)** — no free Arkham-class graph.

---

## What this pack is

| Include | Exclude |
|---------|---------|
| Official disclosure URLs | Full multi‑MB/GB address dumps |
| How to download | Third-party label DBs / explorer scrapes |
| Tiny **SAMPLE** file excerpts (schema shape) | Invented entity names |
| OFAC SDN public endpoints | Sanctions ≠ exchange flow labels |

---

## OKX Proof of Reserves

| Kind | URL |
|------|-----|
| PoR hub | https://www.okx.com/proof-of-reserves |
| Download UI | https://www.okx.com/proof-of-reserves/download |
| Verifier repo | https://github.com/okx/proof-of-reserves |
| Example Reserves ZIP (observed 2026-09-09) | https://static.okx.com/cdn/okx/por/chain/por_csv_2026081100_V6.zip |

**Parse tip:** Reserves ZIP → CSV. Skip coin-totals block; address table header includes `coin,Type,Network,...,address,amount,message,signature...`.

**Sample (truncated):** see `samples/okx_por_addresses_SAMPLE.csv` in this pack directory.

---

## BitMEX PoRL

| Kind | URL |
|------|-----|
| Dashboard | https://www.bitmex.com/app/porl |
| Public listing | https://public.bitmex.com/?prefix=data/porl/ |
| S3 list API | https://s3-eu-west-1.amazonaws.com/public.bitmex.com?list-type=2&prefix=data/porl/ |
| Example BTC reserves YAML | https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260908-reserves-966053-20260908D100102534828000.yaml |
| Example token_reserves YAML | https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260827-token_reserves-20260827.yaml |
| Verifier repo | https://github.com/BitMEX/proof-of-reserves-liabilities |

**Parse tip:** Reserves YAML `address:` list with `addr`, `addr_type`, `balance`. Liabilities CSVs are **not** exchange address seeds.

**Sample:** `samples/bitmex_reserves_SAMPLE.yaml`

---

## Binance Proof of Reserves / wallet addresses

| Kind | URL |
|------|-----|
| PoR page | https://www.binance.com/en/proof-of-reserves |
| PoR page (alt host) | https://www.binance.info/en/proof-of-reserves |
| Audit time list (public apex) | https://www.binance.com/bapi/apex/v1/public/apex/market/query/auditProofSnapshotCondition |
| Snapshot metadata (POST) | https://www.binance.com/bapi/apex/v1/public/apex/market/query/userReserveAuditProofSnapshot |
| Resolve ZIP (GET `auditId`) | https://www.binance.com/bapi/apex/v1/public/apex/market/por/getDownloadUrl?auditId=PR01SEP26 |
| Example CDN ZIP (observed) | https://public.bnbstatic.com/static/proof-of-reserve/wallet_address_20260901.zip |

**Parse tip:** ZIP contains `*_HotCold.csv` and `*_Deposit.csv` with header `coin,network,address,balance,Height,Third party custodian name`. Use only published fields.

**Sample:** `samples/binance_hotcold_SAMPLE.csv` (prefer HotCold for exchange-wallet shape). Deposit CSV is millions of rows — do not paste into Grok.

---

## OFAC (sanctions seeds — not exchange flow)

| Kind | URL |
|------|-----|
| OFAC home | https://ofac.treasury.gov/ |
| SDN list page | https://ofac.treasury.gov/specially-designated-nationals-and-blocked-persons-list-sdn-human-readable-lists |
| SDN advanced XML/CSV downloads | https://www.treasury.gov/ofac/downloads/sdn.csv (and related files on treasury.gov/ofac/downloads/) |
| Alternative index | https://ofac.treasury.gov/sanctions-list-service |

**Helix use:** Boolean hit / compliance flag only. **Not** a substitute for exchange PoR labels. Refresh on a documented cadence; cache locally — do not hammer Treasury.

**Sample:** Do not embed full SDN here. Grok should fetch the official CSV header + 2 EXAMPLE rows only when needed, labeled EXAMPLE.

---

## Suggested Grok prompt (copy-paste)

```
You are helping Helix labeled-flow seed design (paper / live-capable research — no trading).

Official PoR sources only: OKX, BitMEX, Binance (URLs in the Helix PoR/OFAC pack). OFAC SDN is sanctions-only.

Tasks:
1) Summarize how to refresh each venue’s address list from the official URLs.
2) Propose a schema: seed_source, venue, address, network/coin, asof, quality_flag — no invented entity_name.
3) Explain join to RPC transfers (Alchemy eth_call-only later) without claiming whale identity.
4) Mark anything unofficial as OUT OF SCOPE.

Never invent addresses or labels. If a dump isn’t attached, use URLs + SAMPLE excerpts only.
```

---

## Operator note (box-local full dumps)

Full files (not for Grok/community git):

- `helix-cowork/proof/por/okx_por_csv_*.zip`
- `helix-cowork/proof/por/bitmex_*-reserves-*.yaml`
- `helix-cowork/proof/por/binance_wallet_address_*.zip`

Detailed provenance: `helix-cowork/notes/por-seeds-2026-09-09.md`  
Cloud Agent wire brief: `helix-cowork/briefs/brief-01-por-ofac.md`

---

## Publish target

**helix-community** (public docs): copy this folder’s markdown + `samples/*` only.  
Do **not** commit full PoR ZIPs to public git.
