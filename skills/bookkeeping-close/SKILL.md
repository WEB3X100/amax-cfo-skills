---
name: bookkeeping-close
description: Bookkeeping health and month-end close. Use for "bookkeeping status", "close checklist", "where are we on the close", "month-end", "what's uncategorized", or "ready for theBPO".
---

# Bookkeeping Status & Month-End Close

Target: close in **4–5 business days** (was 2–3 weeks). theBPO posts from 1 Oct 2026 onward; QBO cutoff for history was 30 Sep 2026.

## Health check (pull live)
1. QBO P&L for the month + YTD; Balance Sheet as of month end.
2. Flags to compute:
   - Income in generic buckets ("Services", "Not specified") — $ and % of revenue.
   - COGS posted to "(deleted)" accounts or missing COGS for months with revenue.
   - Opex suspiciously low (< $1,000/month) → expenses not entered.
   - Uncategorized Asset / Income / Expense, Opening Balance Equity, Ask My Accountant balances.
   - A/R vs Airtable outstanding gap (unapplied payments).
   - Deferred revenue not released for departed groups.
   - Bank registers vs bank feed gaps per account.
   - Shareholder Advance – Maaz movement.
3. Score each 🟢/🟡/🔴.

## Close checklist (Day 1–5)
| Day | Task | Owner |
|---|---|---|
| D1 | Accept/match all bank & card feeds; upload statements | Sara / theBPO |
| D1 | Enter all vendor bills (Amax USA, airlines/BSP, hotels, Mawasim, Rezlive) with Class | Sara |
| D2 | Apply client payments to invoices; clear unapplied | Sara |
| D2 | Release deferred revenue for groups departed this month | theBPO (Maaz approves departure list) |
| D3 | Reconcile Chequing, Trust, Houston Clearing, Amex | theBPO |
| D3 | Distributor settlements & commissions | Sara / Maaz |
| D4 | Accruals, prepaid (Amax USA), HST review | theBPO |
| D4 | Review P&L by Class, margin per line, variance vs last month | AMAX CFO bot → Maaz |
| D5 | Sign-off, lock period, update Airtable `21_MONTHLY_METRICS` | Maaz |

## Output
1. Close status: Day N of 5, % complete, blockers.
2. Flag table with $ impact.
3. Who needs to do what today.
4. For Maaz only: yellow-field inputs he must provide (departure dates, approvals).
