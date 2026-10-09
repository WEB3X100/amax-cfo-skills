---
name: deferred-revenue
description: Reconcile customer prepayments and invoiced bookings to deferred revenue, then prepare recognition candidates from fulfilled travel evidence. Use for unearned revenue, travel-date recognition, deferred-revenue rollforwards, or month-end recognition exceptions. Never post recognition without controller approval.
example-prompt: Build the deferred-revenue rollforward and show bookings eligible for recognition this month with evidence gaps.
---

# Deferred Revenue

## Outcome

Explain what remains unearned, what may be recognized, and what evidence blocks recognition without confusing bookings, cash collections, and accounting revenue.

## Source contract

- QuickBooks owns posted invoices, payments, credits, deferred-revenue balances, and recognized-revenue entries.
- Command Center owns booking, traveler, product, service, and fulfillment evidence.
- The approved accounting policy owns recognition rules.
- Twenty CRM may provide pre-sale context but cannot authorize revenue recognition.

An invoice, a cash receipt, or a planned travel date alone does not authorize recognition.

## Procedure

1. Confirm entity, currency, reporting period, approved recognition policy, and QuickBooks deferred-revenue control account.
2. Build an opening balance from QuickBooks and retain the report or transaction identifiers used.
3. Link additions to operational bookings using stable booking, invoice, customer, product, amount, and currency identifiers.
4. Identify recognition candidates only when the required service or fulfillment evidence exists.
5. Calculate candidate recognition by the approved policy. Keep partially fulfilled and multi-component bookings separated.
6. Reconcile opening balance plus additions minus posted recognition and other approved adjustments to the ending QuickBooks balance.
7. Queue unmatched balances, missing travel dates, canceled or changed bookings, unposted payments, amount differences, and missing fulfillment evidence.
8. Prepare a proposed entry packet with source references and a unique idempotency key; do not post it.

## Required output

- Period, entity, policy version, sources, and confidence.
- Rollforward: opening, additions, recognized, adjustments, ending, and unexplained difference.
- Recognition candidates with booking, invoice, product, service date, evidence, amount, and rationale.
- Deferred balances by expected service month and product.
- Exception queue with owner, required evidence, and next action.
- Proposed journal-entry packet marked `DRAFT — NOT POSTED`.

## Approval boundary

Never change a travel date, recognition rule, invoice, deferred balance, class, department, or journal entry without controller approval. If posting is later authorized, use the approved idempotency key, write once, and read the QuickBooks record back.
