---
name: ar-collections
description: Receivables and collections. Use for "who owes us", "overdue clients", "A/R aging", "collections list", "days to recover payment", "send reminders", or early-payment incentive questions.
---

# A/R & Collections

## Pull
1. QBO **A/R Aging Summary** and **A/R Aging Detail** (as of today).
2. Airtable `10_PAYMENT SCHEDULE`: Days Overdue > 0 or Days Until Due ≤ 7, with linked `01_BOOKINGS` (Booking Type, Travel Date, Distributor) and `00_CLIENTS` (name, preferred language, WhatsApp — never passport/DOB).
3. Airtable `23_COMMUNICATIONS LOG`: last contact date per client.
4. CRM: client status (VIP / repeat / first-time).

## Reconcile before reporting
- Compare QBO open A/R to Airtable outstanding for the same client. If QBO is higher, the likely cause is **payments received but not applied** in QBO (known issue) — label these "Unapplied? check deposits" rather than chasing the client.
- Exclude clients whose payment is already in the bank but unmatched.

## Prioritise (score each client)
- Amount overdue (largest first)
- Days to travel (≤45 days = top priority; vendor money is at risk)
- Days overdue bucket: 1–30 / 31–60 / 61–90 / 90+
- Distributor-booked → chase the distributor, not the traveller (Model 2 remits full amount; Model 1 remits agreed net amount)

## Output
1. Headline: total overdue $, # clients, amount tied to departures in next 45 days.
2. Top 10 table: Client | Booking | Type | Overdue $ | Days overdue | Travel date | Last contact | Channel | Suggested tone.
3. Draft messages (WhatsApp + email) per tone:
   - **Gentle** (good payer, <15 days): friendly reminder + payment link.
   - **Firm** (repeat late or >30 days): due date, amount, consequence (seat/visa/hotel release per terms).
   - **Distributor**: statement-style list of their open bookings.
   Match preferred language when known (English / Urdu / Arabic).
4. Optional early-payment incentive: suggest offer from `14_EARLY_PAYMENT_INCENTIVES` pattern (e.g., small discount for paying balance ≥30 days early) — only where travel is >60 days out.

## Writes (approval required)
- Create QBO payment link or send invoice reminder → show the invoice #, amount, recipient, then wait for "yes".
- Log each sent reminder to `23_COMMUNICATIONS LOG` after staff confirm it was sent.

## KPI to report monthly
Collection rate % (paid vs due), DSO, average days-to-recover by booking type and by distributor.
