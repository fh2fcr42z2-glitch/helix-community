# Helix PoR / OFAC seeds — Grok-readable pack

**Why this exists:** Grok cannot read files on the Helix box (`/workspace/...`). Use this **GitHub** doc + linked **official CDN/Treasury URLs** instead.

**Rule:** Official Proof-of-Reserves / transparency seeds only. Never invent wallet labels or entity graphs. Missing seed → DARK.

Helix labeled-flow goal: `PoR/OFAC seeds ⨝ RPC` (RPC join is follow-on). Paper research / live-confidence scaffolding — no unsupervised live orders.

---

## Official seed URLs (fetch these)

### OKX Proof of Reserves
- Hub: https://www.okx.com/proof-of-reserves
- Download UI: https://www.okx.com/proof-of-reserves/download
- Example Reserves ZIP (addresses CSV inside): https://static.okx.com/cdn/okx/por/chain/por_csv_2026081100_V6.zip
- Verifier: https://github.com/okx/proof-of-reserves
- Observed address rows in Aug 11 2026 V6 CSV after address header: **212,442**
- CSV address header: `coin,Type,Network,Snapshot Height,address,amount,message,signature1,signature2,...`

### BitMEX PoRL
- Dashboard: https://www.bitmex.com/app/porl
- Listing: https://public.bitmex.com/?prefix=data/porl/
- S3 list: `https://s3-eu-west-1.amazonaws.com/public.bitmex.com?list-type=2&prefix=data/porl/`
- Verifier: https://github.com/BitMEX/proof-of-reserves-liabilities
- Reserves YAML keys look like `YYYYMMDD-reserves-<height>-<id>.yaml` with `address.addr` fields

### Binance Proof of Reserves
- Page (try `.info` if `.com` HTML empty): https://www.binance.info/en/proof-of-reserves
- Also: https://www.binance.com/en/proof-of-reserves
- Wallet address ZIPs are published via Binance public CDN / apex APIs (resolve current ZIP from official PoR page — do not invent addresses)
- Example staged dump name pattern: `binance_wallet_address_YYYYMMDD.zip` containing HotCold + Deposit CSVs

### OFAC SDN (compliance seed, not a whale graph)
- SDN CSV: https://www.treasury.gov/ofac/downloads/sdn.csv
- SDN advanced / related downloads: https://ofac.treasury.gov/sanctions-list-data
- Cache on disk; refresh politely; document as-of date

---

## Samples in this folder (small)

| File | What |
|------|------|
| `samples/bitmex-reserves-sample.yaml` | Real BitMEX reserves YAML snapshot (small) |
| `samples/bitmex-token-reserves-sample.yaml` | BitMEX token reserves YAML (small) |
| `samples/okx-por-address-header-sample.csv` | OKX address-table header + ~25 rows (not full dump) |

Full OKX/Binance ZIPs are too large for casual chat — **pull from official CDN URLs above**.

---

## Prompt for Grok (paste)

```
You are Helix Data Architect. Read the Helix PoR/OFAC seed pack on GitHub (this README and samples/). Using ONLY official OKX / BitMEX / Binance PoR URLs and OFAC SDN:

1) Summarize how to ingest each seed into SQL tables: seed_por_address(venue, network, address, asof_ts, source_url, quality_flag), seed_ofac_sdn(...).
2) Parse the BitMEX YAML sample and count addresses.
3) Parse the OKX CSV sample header and list columns.
4) Propose a labeled-flow health API that stays DARK until seeds load; never invent entity names.
5) DDL + quality_flag PASS/WARN/FAIL rules.

Do not invent addresses. Do not claim whale identity. Helix is live-capable research; no unsupervised live orders.
```

---

## Related Helix repos

- Private desk: https://github.com/fh2fcr42z2-glitch/helix-cx
- Public docs: https://github.com/fh2fcr42z2-glitch/helix-community


### Additional sample (2026-09-09 republish)
- [binance-hotcold-sample.csv](./samples/por/binance-hotcold-sample.csv) — truncated HotCold header + rows (full ZIP stays operator-local)
