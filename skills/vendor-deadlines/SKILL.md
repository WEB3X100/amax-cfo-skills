---
name: vendor-deadlines
description: Vendor payment deadline guard. Use for "what do we owe vendors", "Amax USA payments", "bills due", "A/P", "vendor deadlines", "Hajj instalments", BSP/IATA settlement, or "can we pay X this week".
---

# Vendor Deadlines & A/P

## Pull
1. Airtable `11_VENDOR OBLIGATIONS` (tblldSZly8eFhtenW): all Payment Status ≠ Paid; fields Vendor, Component, Amount Due, Due Date, Days Until Due, Alert Level, Related Booking.
2. QBO **A/P Aging Summary + Detail**.
3. Linked bookings: Travel Date, Total Paid vs Total Invoice (is the client paid up enough to fund this?).

## Deadline rules (Amax-specific)
- **Umrah – Amax USA (hotel + transport + visa):** due 30 days before departure. Hard deadline.
- **Umrah – flights:** fund at booking (≈50% of invoice collected upfront to lock fares).
- **Hajj – Amax USA:** monthly instalments June → November for the following year's Hajj.
- **Tours:** vendor payment 30–60 days before departure.
- **Air ticketing (BSP/IATA via Sabre):** BSP settlement cycle — flag anything on the BSP statement not matched in QBO.

## Output
1. Headline: total due next 7 / 14 / 30 days; # items 🔴.
2. Table sorted by Days Until Due: Vendor | Component | Booking | Amount (CAD / USD) | Due | Days | Client funded %? | Alert.
3. **Funding check:** for each item, compare to Net True Available Cash (use cash-position skill). Mark "UNFUNDED" if cash can't cover it.
4. Mismatches: obligations in Airtable not in QBO A/P (bill not entered) and QBO bills with no Airtable obligation.
5. Actions: who pays what by when.

## Alerts
- 14 days → 🟡 to Maaz.
- 7 days → 🔴 to Maaz + Sara.
- Overdue → 🔴 every morning until Paid with Payment Reference filled.

## Never
- Never mark an obligation Paid without a payment reference and date from a human.
- Never initiate a payment.

## FX
Amax USA is billed in USD. Show CAD at today's rate and note exposure if CAD has weakened since the package was priced.
