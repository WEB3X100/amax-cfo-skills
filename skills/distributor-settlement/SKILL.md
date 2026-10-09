---
name: distributor-settlement
description: Reconcile and prepare a settlement statement for an agent, distributor, or partner using the current approved agreement. Use for partner balances, commissions, booking allocations, credits, refunds, or settlement disputes. Never infer commercial terms or expose banking details.
example-prompt: Prepare this partner's settlement statement for the period and isolate every booking or payment exception.
---

# Distributor Settlement

## Outcome

Produce an auditable settlement packet whose booking population, contractual calculation, payments, and exceptions can be reviewed before any money or ledger record changes.

## Source contract

- The current approved partner agreement owns commission, markup, allocation, timing, refund, and currency rules.
- Command Center owns booking and fulfillment detail.
- QuickBooks owns posted invoices, bills, credits, payments, and accounting balances.
- Prior approved settlements provide opening items, not permission to reuse expired terms.

If the applicable agreement or version is unavailable, stop the calculation and return `AGREEMENT_REQUIRED`.

## Procedure

1. Confirm partner identity, legal entity, settlement period, currencies, agreement version, and authorized recipients.
2. Build the eligible booking population from Command Center using stable booking identifiers.
3. Apply the agreement's formula line by line. Keep taxes, fees, commissions, markups, credits, and refunds distinct.
4. Match QuickBooks invoices, bills, credits, and payments to each booking or approved adjustment.
5. Bring forward only documented prior-period open items.
6. Keep currencies separate unless an approved exchange-rate source and conversion policy are supplied.
7. Reconcile gross activity through payments and credits to the proposed closing balance.
8. Queue missing bookings, duplicates, amount or currency differences, cancellations, disputed service, missing approvals, and unmatched cash.

## Required output

- Partner, period, entity, agreement version, sources, and confidence.
- Booking-level settlement table with formula inputs and source references.
- Opening items, current activity, payments, credits, adjustments, and closing balance.
- Currency-specific totals and any approved conversion method.
- Exception queue with owner, evidence required, and recommended next action.
- Partner-facing statement draft marked `NOT SENT` with no bank-account details.

## Approval boundary

Never change commercial terms, approve a commission or refund, post a bill or credit, release payment, alter banking details, or send the statement without exact human authorization. Read back any later approved QuickBooks mutation.
