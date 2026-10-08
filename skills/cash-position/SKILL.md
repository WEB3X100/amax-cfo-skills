---
name: cash-position
description: Daily cash brief and Net True Available Cash. Use when asked "how much cash do we have", "cash position", "morning brief", "can we afford X", "runway", or "90-day cash forecast".
---

# Cash Position & Net True Available Cash

## Inputs to pull
1. **QBO Balance Sheet** (as of today): RBC Business Chequing 3598, RBC TICO Trust 7821, AMAX Houston Collections Clearing, Amex Aeroplan card balance.
2. **QBO Balance Sheet liabilities**: Deferred Revenue – Hajj Deposits, Deferred Revenue – Umrah Packages, A/P.
3. **Airtable `11_VENDOR OBLIGATIONS`** (tblldSZly8eFhtenW): Payment Status ≠ Paid, Due Date within 0–90 days.
4. **Airtable `10_PAYMENT SCHEDULE`** (tblT66r6b2AaDheFi): Payment Status ≠ Paid, Due Date within 0–90 days (expected inflows).
5. **Airtable `13_CASH FLOW PROJECTION`** (tblUefVqlWaOwtmem) if current periods exist.

## Calculation
```
Gross Cash            = Chequing + Trust + Houston Clearing
Restricted (Trust)    = Trust balance (client money — TICO)
Deferred Revenue      = Hajj deposits + Umrah packages (+ Tours if present)
Vendor Due ≤30d       = sum of unpaid vendor obligations due in next 30 days
Net True Available    = Gross Cash − Deferred Revenue owed to vendors not yet paid − Vendor Due ≤30d − Card balance due
```
If deferred revenue exceeds gross cash, say so plainly: deposits have already been used as working capital — this is the restricted-fund shortfall.

## Output format
1. One line: **Net True Available Cash: $X (🟢/🟡/🔴)** vs Gross Cash $Y.
2. Table: Account | Balance | Restricted? | Source/as-of.
3. Next 30/60/90 days: Expected inflows | Vendor outflows | Net | Cumulative. Flag any period that goes negative 🔴.
4. Top 3 vendor deadlines (amount, vendor, booking, days left).
5. Top 3 inflows at risk (overdue clients).
6. "What I'd do next" — max 3 actions with owner.

## Thresholds
- 🔴 Net True Available < 0, or any 30-day window negative, or any vendor obligation ≤7 days unfunded.
- 🟡 Net True Available < $25,000 or a vendor obligation ≤14 days.
- 🟢 otherwise.

## Emergency protocol (if 🔴)
List overdue clients by amount, the top 5 to call today, vendor items that could be deferred, and recommend Maaz review the line of credit. Recommend daily re-runs until stable.

## Notes
- If QBO bank registers lag the bank feed (known issue Jun–Sep 2026), say "QBO register vs feed differs by $X" and show both.
- Never imply Trust money can fund opex or other departures.
