---
name: qbo-reconcile
description: Bank and card reconciliation prep against QuickBooks. Use for "reconcile RBC for <month>", "bank rec", "trust account rec", "Amex rec", "why doesn't QBO match the bank", or "unmatched transactions".
---

# QBO Reconciliation Prep

Reconciliation **sign-off stays in the QBO UI** (Sara / theBPO). This skill finds, matches and explains.

## Accounts in scope
| Account | QBO name | Notes |
|---|---|---|
| RBC Business Chequing 3598 | RBC Chequing | operating |
| RBC TICO Trust 7821 | TICO Trust | client funds — restricted |
| Houston Collections Clearing | AMAX Houston Collections Clearing | typed as bank; really a clearing account |
| Amex Aeroplan Business Reserve | Amex 1004 / 2004 | card |

## Steps
1. Ask (or infer) account + month. Get statement ending balance from the user or uploaded statement.
2. Pull QBO balance for that account at month end (Balance Sheet as of last day).
3. Pull QBO transactions for the period (via report or import data available) and the statement lines provided.
4. Match on amount + date ±3 days + payee. Classify unmatched:
   - **In bank, not in QBO** → needs entry (suggest account + Class).
   - **In QBO, not in bank** → possible duplicate or wrong account (e.g., Hajj receipts keyed to Chequing that actually landed in Trust/Houston).
   - **Timing** → outstanding cheques/deposits in transit.
5. Produce the reconciliation: Statement balance ± outstanding items = Adjusted bank; QBO balance ± corrections = Adjusted book; Difference (must be 0.00).

## Suggested coding
- Class = revenue line (Umrah / Hajj / Air Ticketing / Vacations-Tours / Visa & Biometric / Ancillary).
- Location = channel (Retail vs Distributor/B2B) — confirm with Maaz if not yet set.
- Client receipts for future departures → Deferred Revenue (Hajj Deposits / Umrah Packages), never income.

## Output
1. Headline: Difference $X; # unmatched items both sides.
2. Rec table (statement → adjusted bank; book → adjusted book).
3. Unmatched lists with suggested action + account + Class.
4. "Human decisions needed" list — anything ambiguous.
5. Optional CSV for QBO import (only after approval).

## Watch-outs (known 2026 issues)
- QBO registers lagged the bank feed Jun–Sep 2026; accept/match feed before reconciling.
- 14 Hajj receipts (~$237K) keyed to Chequing in Aug–Sep likely belong in Trust/Houston — re-point, don't duplicate.
- QBO fiscal year ends 31 July — retained earnings roll on 1 Aug.
