---
name: investigate
description: Ad-hoc financial investigation. Use for "why did X change", "margin by product/line", "Umrah margin this quarter", "trace this amount", "variance", "compare months", "which line makes the most money", "sales by customer".
---

# Financial Investigation

## Method
1. **Restate the question** as a measurable one (metric, period, comparison).
2. **Pull** the narrowest QBO report that answers it: P&L (by month), Sales by Product, Sales by Customer, A/R or A/P detail, Balance Sheet by month. Add Airtable bookings/packages for volume and price drivers.
3. **Decompose** the change:
   - Revenue = volume (# bookings / pax) × price (avg booking value) × mix (Hajj/Umrah/Air/Tours).
   - Margin = revenue − matching vendor cost (Class-tagged). If COGS is missing or on deleted accounts, say margin is unreliable and show booking-level margin from Airtable `01_BOOKINGS` (Gross Margin $, Margin %) instead.
   - Timing effects: deferred revenue releases, fiscal-year roll (31 Jul), double-counted months.
4. **Trace** a specific amount: find every account it appears in, the transaction(s), date, payee, and whether a matching opposite entry exists.
5. **Conclude** with drivers ranked by $ impact and confidence (High / Medium / Low).

## Output
- Answer in one sentence.
- Bridge table: Start → driver 1 → driver 2 → … → End.
- Data-quality caveats that could change the answer.
- Next step (one).

## Seasonality context
- Hajj: sales April–September, instalments Jun–Nov, travel the following June–July.
- Umrah: year-round; peak Ramadan.
- December is a booking month for Feb–Apr travel.
- Air ticketing: steady; margin = commission/service fee $20–$150/ticket.
