# PoR / transparency address seed sources — 2026-09-09

**Purpose:** Official Proof-of-Reserves / transparency address seeds for Helix labeled-flow (paper research only).  
**Scope venues:** OKX, BitMEX, Binance — **official sources only**.  
**Rule:** Never invent wallet labels. Third-party aggregators, explorer tags, and unofficial label DBs are **OUT OF SCOPE**.  
**Collected:** 2026-09-09 (box UTC; user zone America/Chicago = CT).  
**Artifacts dir:** `/workspace/helix-cowork/proof/por/`

---

## Summary

| Venue | Official disclosure pages | Address list format | Download from box | Saved under `proof/por/` |
| --- | --- | --- | --- | --- |
| OKX | PoR + PoR download | ZIP → CSV (addresses + signatures) | **OK** (HTTP 200) | `okx_por_csv_2026081100_V6.zip` (37M) |
| BitMEX | PoRL dashboard + `public.bitmex.com` S3 | YAML reserves (+ optional token_reserves YAML; liabilities CSV) | **OK** (S3 HTTP 200) | `bitmex_20260908-reserves-…yaml` (22K); `bitmex_20260827-token_reserves-…yaml` (8.3K) |
| Binance | PoR page + public apex APIs + `public.bnbstatic.com` ZIP | ZIP → CSV (`HotCold` + `Deposit`) | **OK** via resolved CDN URL | `binance_wallet_address_20260901.zip` (113M) |

**Seed URL count (official, cited below):** **18** distinct seed/provenance URLs (pages + listing + direct file/API endpoints).  
**Blockers:** None for address-list download on these three venues from the box on 2026-09-09.  
Note: bare `https://www.binance.com/en/proof-of-reserves` HTML sometimes returned empty from this box; `https://www.binance.info/en/proof-of-reserves` and the public `bapi/apex/...` endpoints worked. Direct CDN ZIP did not require login.

---

## 1. OKX (official)

### Pages
- PoR hub: https://www.okx.com/proof-of-reserves  
- PoR file download UI: https://www.okx.com/proof-of-reserves/download  
- US locale mirror of download UI: https://www.okx.com/en-us/proof-of-reserves/download  
- Open-source verifier tooling (official OKX GitHub): https://github.com/okx/proof-of-reserves  
- How-to (ownership / balance verify): https://www.okx.com/en-us/help/how-to-verify-okx-ownership-and-balance-of-the-wallet-address  

### How to download address lists
1. Open the **Reserves** tab on the download page (not Liability — liability zips are zk-STARK proof data, not the public address CSV).  
2. Each Reserves row links a ZIP on `static.okx.com`, pattern:  
   `https://static.okx.com/cdn/okx/por/chain/por_csv_YYYYMMDDHH_Vx.zip`  
3. Unzip → single CSV. Address section header (observed):  
   `coin,Type,Network,Snapshot Height,address,amount,message,signature1,signature2,redeem script/ public key,EOA1,EOA2`  
4. CSV also starts with a coin totals block (`coin,amount`) before the address table — parsers must skip to the address header.

### Latest Reserves ZIP URLs observed on download page (2026-09-09 fetch)
| Report ID | Date (UTC+8) | Direct URL |
| --- | --- | --- |
| 500375535 | Aug 11, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026081100_V6.zip |
| 499955235 | Jul 7, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026070700_V3.zip |
| 508399035 | Jun 19, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026061900_V3.zip |
| 506872725 | May 7, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026050700_V4.zip |
| 507918525 | Apr 20, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026042000_V3.zip |
| 500137125 | Mar 3, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026030319_V3.zip |
| 502892925 | Feb 4, 2026 | https://static.okx.com/cdn/okx/por/chain/por_csv_2026020419_V4.zip |

Liability (Merkle/zk) zips are under `https://static.okx.com/cdn/okx/por/merkel/por_<ReportID>_proof_data.zip` — useful for PoR verification, **not** primary address seeds.

### Saved copy
- `/workspace/helix-cowork/proof/por/okx_por_csv_2026081100_V6.zip`  
  - Source URL: `https://static.okx.com/cdn/okx/por/chain/por_csv_2026081100_V6.zip`  
  - HTTP 200; ~37 MB zip → `okx_por_2026081100_V6.csv` (~75 MB)  
  - Address rows (post address-header): **212,442**  
- Provenance: HTML/SSR `auditList` on official download page + direct CDN GET.

### Status
**FREE official disclosure — downloaded successfully.**

---

## 2. BitMEX (official)

### Pages / listing
- PoRL dashboard: https://www.bitmex.com/app/porl  
- Public data browser: https://public.bitmex.com/?prefix=data/porl/  
- S3 list API (machine-readable): `https://s3-eu-west-1.amazonaws.com/public.bitmex.com?list-type=2&prefix=data/porl/`  
- Object base: `https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/<filename>`  
  (also reachable as `https://public.bitmex.com/data/porl/<filename>` once key is known)  
- Official verifier repo: https://github.com/BitMEX/proof-of-reserves-liabilities  
- Official blog (method + historical example object): https://www.bitmex.com/blog/proof-of-reserves-liabilities-bitmex-demonstration  

### How to download address lists
1. List keys via S3 `list-type=2&prefix=data/porl/` (paginate with `continuation-token` while `IsTruncated=true`).  
2. **BTC reserves addresses:** keys matching `YYYYMMDD-reserves-<height>-<id>.yaml` — YAML with `address:` list (`addr`, `addr_type`, `balance`, `script`).  
3. **Token / multi-chain reserves (when published):** `YYYYMMDD-token_reserves-YYYYMMDD.yaml`.  
4. **Liabilities:** large `*-liabilities-*.csv` — Merkle liabilities for user verification, **not** exchange wallet address seeds (keep out of address-seed ingest unless separately needed).  
5. Inventory on 2026-09-09 listing pass: **5,419** keys under `data/porl/` (~484 reserves YAMLs, ~372 liabilities CSVs).

### Latest objects used as seeds (from S3 listing)
| Kind | Key | Direct URL |
| --- | --- | --- |
| BTC reserves YAML | `data/porl/20260908-reserves-966053-20260908D100102534828000.yaml` | https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260908-reserves-966053-20260908D100102534828000.yaml |
| Token reserves YAML (newest listed) | `data/porl/20260827-token_reserves-20260827.yaml` | https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260827-token_reserves-20260827.yaml |

### Saved copies
- `/workspace/helix-cowork/proof/por/bitmex_20260908-reserves-966053-20260908D100102534828000.yaml` — HTTP 200, ~22 KB; **79** BTC `addr` entries in this snapshot.  
- `/workspace/helix-cowork/proof/por/bitmex_20260827-token_reserves-20260827.yaml` — HTTP 200, ~8.3 KB; per-chain token address maps (small set of venues addresses in this file).  
- Provenance: official BitMEX public bucket + GitHub README pointing at `https://public.bitmex.com/?prefix=data/porl/`.

### Status
**FREE official PoRL YAMLs on `public.bitmex.com` — downloaded successfully.**  
Liabilities CSVs intentionally not saved here (not address seeds).

---

## 3. Binance (official)

### Pages
- PoR page: https://www.binance.com/en/proof-of-reserves  
- PoR page (info host, worked from box): https://www.binance.info/en/proof-of-reserves  
- UI shows **Download All Address** (no login required for this control in public apex flow).  
- Academy overview (official): https://academy.binance.com/en/articles/what-is-proof-of-reserves-and-how-it-works-on-binance  

### How to download address lists (official public API → CDN ZIP)
Observed front-end (`bin.bnbstatic.com` PoR page chunk) calls:

1. **List audit times** (GET):  
   `https://www.binance.com/bapi/apex/v1/public/apex/market/query/auditProofSnapshotCondition`  
   (also works on `www.binance.info`)  
   Returns strings like: `01/09/26 00:00:00 UTC | BTC Block Height 964957`.

2. **Snapshot metadata + `auditId`** (POST JSON `{time, pageIndex, pageSize}`):  
   `https://www.binance.com/bapi/apex/v1/public/apex/market/query/userReserveAuditProofSnapshot`  
   Example response fields: `auditId` (e.g. `PR01SEP26`), `merkleRootHash`, `snapshotDataList` (per-coin ratios/balances — not the full address book).

3. **Resolve address ZIP URL** (GET):  
   `https://www.binance.com/bapi/apex/v1/public/apex/market/por/getDownloadUrl?auditId=PR01SEP26`  
   Returns CDN URL, e.g.:  
   `https://public.bnbstatic.com/static/proof-of-reserve/wallet_address_20260901.zip`

4. Download that ZIP (CSV inside). Observed members for `PR01SEP26`:
   - `PR01SEP26_HotCold.csv` — header: `coin,network,address,balance,Height,Third party custodian name` (**1,364** data rows)  
   - `PR01SEP26_Deposit.csv` — same header (**4,181,656** data rows)

### Direct download URL used (official CDN)
- https://public.bnbstatic.com/static/proof-of-reserve/wallet_address_20260901.zip  

### Saved copy
- `/workspace/helix-cowork/proof/por/binance_wallet_address_20260901.zip` — HTTP 200, ~113 MB.  
- Provenance chain: official PoR page JS → public apex `getDownloadUrl` → `public.bnbstatic.com` ZIP.  
- Labels in CSV are **only** what Binance publishes (coin/network/optional third-party custodian name). Do not invent Helix labels beyond official fields.

### Status
**FREE official transparency/PoR address ZIP — downloaded successfully.**  
Blocker note: initial empty HTML from `www.binance.com/en/proof-of-reserves` on this box; use `binance.info` and/or apex APIs + CDN as above. No API secrets used.

---

## Saved files inventory (`/workspace/helix-cowork/proof/por/`)

| File | Bytes (approx) | Venue | Format |
| --- | --- | --- | --- |
| `okx_por_csv_2026081100_V6.zip` | 37M | OKX | ZIP→CSV addresses |
| `bitmex_20260908-reserves-966053-20260908D100102534828000.yaml` | 22K | BitMEX | YAML BTC reserves addresses |
| `bitmex_20260827-token_reserves-20260827.yaml` | 8.3K | BitMEX | YAML token reserves addresses |
| `binance_wallet_address_20260901.zip` | 113M | Binance | ZIP→CSV HotCold + Deposit |
| `README.md` | small | meta | pointer to this note |

---

## OUT OF SCOPE (do not use as Helix seeds)

- ChainQuery / other third-party PoR scrapes or label DBs  
- Unofficial “exchange wallet” lists on explorers (Etherscan tags, etc.) unless independently published by the venue  
- Academic/blog appendices that rehost files (e.g. secondary writeups) — cite only for navigation; prefer venue URLs above  
- Liability-only Merkle dumps when the goal is **address** seeds (OKX liability zips; BitMEX liabilities CSVs)  
- Any non-OKX / non-BitMEX / non-Binance venue  
- Invented or inferred wallet labels beyond fields present in official files  

---

## Seed URL checklist (count = 18)

1. https://www.okx.com/proof-of-reserves  
2. https://www.okx.com/proof-of-reserves/download  
3. https://www.okx.com/en-us/proof-of-reserves/download  
4. https://github.com/okx/proof-of-reserves  
5. https://static.okx.com/cdn/okx/por/chain/por_csv_2026081100_V6.zip  
6. https://www.bitmex.com/app/porl  
7. https://public.bitmex.com/?prefix=data/porl/  
8. https://s3-eu-west-1.amazonaws.com/public.bitmex.com?list-type=2&prefix=data/porl/  
9. https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260908-reserves-966053-20260908D100102534828000.yaml  
10. https://s3-eu-west-1.amazonaws.com/public.bitmex.com/data/porl/20260827-token_reserves-20260827.yaml  
11. https://github.com/BitMEX/proof-of-reserves-liabilities  
12. https://www.bitmex.com/blog/proof-of-reserves-liabilities-bitmex-demonstration  
13. https://www.binance.com/en/proof-of-reserves  
14. https://www.binance.info/en/proof-of-reserves  
15. https://www.binance.com/bapi/apex/v1/public/apex/market/query/auditProofSnapshotCondition  
16. https://www.binance.com/bapi/apex/v1/public/apex/market/query/userReserveAuditProofSnapshot  
17. https://www.binance.com/bapi/apex/v1/public/apex/market/por/getDownloadUrl?auditId=PR01SEP26  
18. https://public.bnbstatic.com/static/proof-of-reserve/wallet_address_20260901.zip  

---

## Report for parent

- **Note path:** `/workspace/helix-cowork/notes/por-seeds-2026-09-09.md`  
- **Seed URLs found:** 18 official  
- **Venues with saved address files:** 3/3 (OKX, BitMEX, Binance)  
- **Blockers:** none for downloads; minor Binance.com HTML empty-response quirk (use `.info` / apex / CDN)  
