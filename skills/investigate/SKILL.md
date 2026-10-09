---
name: investigate
description: Run a bounded, read-only financial investigation when no specialist AMAX CFO skill cleanly applies. Use for a specific unexplained variance, trend, transaction population, or management question. Route to a specialist skill when one covers the request.
example-prompt: Explain the unexpected movement in this account and identify the transactions, operational events, and unresolved residual.
---

# Investigate

## Outcome

Answer one measurable question with a traceable evidence chain, a numeric bridge, and a clear next action without turning an open-ended request into an uncontrolled data search.

## Routing first

Use a specialist skill instead when the request is principally about collections, booking-to-books, close, cash, customer escalation, deferred revenue, distributor settlement, QuickBooks reconciliation, or vendor deadlines.

## Source contract

- QuickBooks owns posted accounting facts.
- Command Center owns booking, fulfillment, payment-schedule, and operational dimensions.
- Twenty CRM owns pre-sale and relationship context.
- Bank or processor evidence owns its direct transaction evidence.
- A mismatch remains visible as an exception.

## Procedure

1. Rewrite the request as one question with entity, period, metric, comparison, and materiality threshold.
2. State the expected decision this investigation should support.
3. Choose the narrowest authoritative dataset and record the query filters and `as_of` time.
4. Establish the control total before adding operational detail.
5. Join operational dimensions using stable identifiers; label fuzzy or manual matches as candidates.
6. Build a bridge from the starting value to the ending value. The bridge must foot or disclose the residual.
7. Test the smallest plausible explanations and separate evidence from inference.
8. Report one of: `EXPLAINED`, `PARTIALLY_EXPLAINED`, `UNEXPLAINED`, or `DATA_REQUIRED`.

## Required output

- Question, decision, scope, materiality, and `as_of` time.
- Sources, filters, record counts, and limitations.
- Numeric bridge with starting value, drivers, ending value, and residual.
- Findings labeled `CONFIRMED`, `SUPPORTED`, or `HYPOTHESIS`.
- Exceptions and missing evidence.
- Recommended next action, owner, and specialist skill if follow-up is needed.

## Approval boundary

This skill is read-only. Never edit source records, post an adjustment, contact a customer or partner, or broaden the investigation into unrelated client data without authorization.
