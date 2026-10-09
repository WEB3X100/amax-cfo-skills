---
name: qbo-reconcile
description: Prove a named QuickBooks account or control total against independent evidence and prepare its exception queue. Use for bank, card, processor, clearing, or subledger reconciliation; not for collections, vendor prioritization, or general close status. Final sign-off belongs to the controller.
example-prompt: Reconcile this account through month-end and show matched items, timing differences, errors, and the unexplained residual.
---

# QuickBooks Reconcile

## Outcome

Prove a QuickBooks balance against independent evidence, isolate every unresolved difference, and make controller sign-off faster without auto-accepting uncertain matches.

## Required inputs

- Entity, QuickBooks account, period end, and materiality or tolerance.
- Independent statement, processor report, bank evidence, or approved subledger control total.
- QuickBooks opening balance, closing balance, and transaction detail for the same scope.

QuickBooks is the accounting system of record, but a reconciliation requires independent evidence. If the evidence is missing, return `EVIDENCE_REQUIRED`.

## Procedure

1. Confirm the period, account, currency, opening balance, closing balance, and evidence cutoff.
2. Normalize dates, amounts, references, and signs without changing source data.
3. Match deterministic identifiers first: transaction ID, check number, processor reference, invoice or bill ID, amount, and currency.
4. Use date-and-amount proximity only to propose a fuzzy candidate. Never label a fuzzy candidate as confirmed without review.
5. Classify remaining items as timing difference, missing in QuickBooks, missing in evidence, duplicate, amount difference, wrong account or class, stale item, or unknown.
6. Build the reconciliation bridge and confirm that matched items plus classified differences explain the control balance.
7. Prepare correction proposals with source references and unique idempotency keys; do not post them.
8. Assign each exception an owner and next evidence or action.

## Required output

- Account, period, entity, currency, sources, cutoff, and tolerance.
- Book balance, evidence balance, reconciled balance, and unexplained residual.
- Confirmed matches and proposed fuzzy matches kept separate.
- Exception queue by class, amount, age, owner, and next action.
- Draft correction packet marked `NOT POSTED`.
- Close status: `READY_FOR_CONTROLLER`, `BLOCKED`, or `IN_PROGRESS`.

## Approval boundary

Never accept a fuzzy match, mark an account reconciled, alter a transaction, post an adjustment, or sign off the close without controller authorization. After an approved correction, read back the QuickBooks record and rerun the affected reconciliation.
