---
name: distributor-settlement
description: Distributor/partner statements and settlements. Use for "what does <distributor> owe", "settlement for Sakina/Darul Hijra/Niyah/Al Raha/RIS", "distributor statement", "commission owed", "partner performance".
---

# Distributor Settlement

## Models
- **Model 1 – Fixed price + markup:** distributor sells at their markup; Amax receives the agreed net price.
- **Model 2 – Commission pass-through:** distributor collects full price, remits all to Amax; Amax pays commission.

## Pull
1. Airtable `03_DISTRIBUTORS` (agreement type, commission %, fixed markup, payment terms) — **never output Bank Details**.
2. Airtable `01_BOOKINGS` filtered by Distributor + month: Total Invoice, Total Paid, Commission Type/Rate/Amount/Status.
3. Airtable `22_DISTRIBUTOR_SETTLEMENTS` for prior unpaid balance.
4. QBO A/R by customer (distributor as customer) and Sales by Customer.

## Statement
```
Bookings this period (list)
Gross booking value
Amount due to Amax (net price or full remittance)
Received from distributor
Commission owed by Amax (Model 2)
Previous unpaid balance
= Net position (distributor owes Amax / Amax owes distributor)
```

## Output
1. One-line net position.
2. Booking-level table.
3. Draft statement message to the distributor (for staff to send).
4. Performance snapshot: bookings, revenue, on-time payment %, trend.
5. Proposed `22_DISTRIBUTOR_SETTLEMENTS` row — written only on approval.

Note: Maqam Umrah relationship is terminated — settle outstanding only, no new bookings.
