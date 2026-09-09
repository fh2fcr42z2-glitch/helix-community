# Helix Market Maker (fork — process only)

Inspiration: public fee-farm / rotate loops (e.g. @0xboan Robinhood token-launch story) + Grok Bot ops hygiene (@bober_smart).  
**Use the loop. PnL stories ($100 → $2,300, iPhone bets) stay DARK — not Helix evidence.**

## What we fork (keep)
1. **Two vaults:** `principal` (do not trade) vs `fee_income` (only tradable paper/live stake).
2. **Launch gate:** check liquidity + holder spread before a launch/listing is worth pushing.
3. **Fee cut:** earn from flow against the market (maker rebate / simulated launch fee) — win or lose for the other side.
4. **Trade only fee income** already collected — never touch starting principal directly.
5. **Entry only when setup absorbs spread cleanly** (exit liquidity / spread budget passes).
6. **Resize next trade from last close** — never a flat fixed bet.
7. **Rotate on a schedule** once the cycle is proven by hand once.

## What we change (Helix — no confusion)
| Viral claim | Helix Market Maker |
|---|---|
| Robinhood token launches | Abstract **venue adapter** (paper first). Real launch/rebate only when a FREE/verified venue exists — else DARK |
| No confirmation / no babysitting for live | **Paper** may auto-rotate under kill switch. **Live money** still needs Call Me X approval (+ `liveOrders` + code kill switch) |
| Unverified $ targets | No target PnL in prompts; success = gates fired correctly + journals |
| One evening → unsupervised | Pilot: 1 hand cycle → paper schedule → live only on explicit go |

## Cycle (every run)
```
LaunchGate(liquidity, holder_spread) 
  → if fail: skip / DARK
  → CollectFeeIncome (paper ledger or venue rebate)
  → SizeFromLastClose(fee_vault only)
  → EntryIfSpreadAbsorbable
  → Exit / rotate
  → Journal (reason, size, vault balances, gate results)
```

## Hard rules
- Principal vault balance is **read-only** for trading paths.
- `HELIX_KILL_SWITCH` or MM kill flag stops new entries in **code**.
- Unknown liquidity / holders / fees → **DARK**, do not invent.
- Fits research loop: LaunchGate∈Research, journal∈Post-mortem, resize∈Fine-tune.
- Fits crew handoff: liquidity veto; size-to-exit; full cycle log.

## Bot hygiene (keep)
- Narrow role: Market Maker owns this loop only.
- Secrets via takeover / secret-request — never chat paste.
- Require approval for live/spend; shared box is **not** a security boundary between bots.

## Out of scope
- Citing viral PnL as backtest or live result
- Unsupervised live rotation by default
- Importing Robinhood as a required dependency without a real adapter + Call Me X approval
