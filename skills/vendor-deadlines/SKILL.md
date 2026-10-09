---
name: vendor-deadlines
description: Prioritize supplier obligations by due date, service risk, contractual consequence, and verified funding. Use for upcoming vendor payments, AP triage, service cutoffs, overdue bills, or which suppliers need action first. Never treat a generic travel deadline as universal policy.
example-prompt: Show supplier obligations requiring action in the next 30 days, including funding gaps and service-at-risk bookings.
---

# Vendor Deadlines

## Outcome

Give finance and operations one deduplicated action queue that protects traveler delivery and cash without replacing QuickBooks AP aging.

## Source contract

- QuickBooks owns posted vendor bills, credits, payments, and AP balances.
- Command Center owns booking-linked supplier commitments, service dates, traveler impact, and operational status.
- The current contract or confirmed supplier term owns deposit, final-payment, cancellation, and release deadlines.
- Verified bank evidence and the approved cash forecast own funding availability.

Never invent a universal number of days before travel. If terms are missing, flag `TERMS_REQUIRED`.

## Procedure

1. Confirm entity, horizon, currencies, and the relevant supplier agreements or confirmed terms.
2. Pull open QuickBooks bills and credits, then link Command Center commitments using stable booking, vendor, bill, amount, currency, and service references.
3. Deduplicate an operational commitment and its posted QuickBooks bill as one economic obligation.
4. Calculate the contractual action date and identify the affected bookings, travelers, and service value.
5. Classify exceptions: commitment not billed, bill without booking, amount or currency mismatch, duplicate, missing term, disputed service, overdue, or already paid operationally but unposted.
6. Compare due obligations with verified unrestricted cash and approved payment priorities.
7. Rank actions by contractual deadline, service-at-risk impact, financial consequence, dispute status, and funding gap.

## Required output

- Horizon, entity, currencies, sources, and evidence freshness.
- Deduplicated obligation queue with vendor, booking, bill, service date, action date, amount, status, and risk.
- Service-at-risk travelers or bookings.
- Funding view using verified unrestricted cash.
- Exception queue with owner, required evidence, and next action.
- Recommended pay, hold, dispute, or escalate decision marked as a recommendation only.

## Approval boundary

Never release payment, mark an item paid, change banking details, alter supplier terms, use protected funds, or contact a supplier without explicit human authorization. Read back any later approved QuickBooks mutation.
