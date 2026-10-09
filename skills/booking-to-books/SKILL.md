---
name: booking-to-books
description: Validate an approved booking and prepare the customer, invoice, payment schedule, deferred-revenue, class/department, and QBO mapping packet. Use for new or changed bookings, invoice preparation, payment schedules, or Command Center-to-QBO posting. Do not use to post without approval.
example-prompt: Prepare the accounting packet for this approved booking and show every missing field or duplicate risk before anything is posted to QBO.
---

# Booking to books

## Outcome

Turn one approved operational booking into a complete, duplicate-safe posting proposal while QBO remains authoritative after creation.

## Source contract

- Twenty supplies approved pre-sale customer and opportunity context.
- Command Center supplies the quote, accepted booking, traveller count, package/service dates, operational invoice, payment schedule, expected costs, owner, and stable internal IDs.
- QBO supplies canonical accounting customer/vendor records, products/services, classes/departments, tax configuration, posted transactions, balances, and returned IDs.

## Required intake

Require: legal payer/customer, booking ID, accepted quote/version, service/package type, service dates, passenger count, invoice currency, approved selling total, tax treatment, payment terms, expected vendor cost and currency, sales/operations owner, and approved class/department mapping.

If any accounting-critical field is missing, list it and stop. Never infer tax treatment, customer identity, class, revenue account, deferred-revenue policy, or exchange rate.

## Procedure

1. Verify the booking is approved and has not been cancelled, superseded, or already posted.
2. Search QBO and the Command Center mapping by stable booking ID, invoice ID, customer identity, and idempotency key. Surface duplicates rather than creating another record.
3. Resolve or propose the QBO customer mapping without copying unnecessary traveller data.
4. Build the invoice proposal from the approved quote. Separate service lines, taxes, currency, class/department, service date, terms, and operational references.
5. Build the payment schedule from approved package terms. Do not use a generic percentage or deposit amount as policy.
6. Apply the controller-approved revenue policy: pre-service customer consideration remains deferred until the approved recognition event. Do not post directly to earned revenue merely because an invoice exists or cash arrived.
7. Compare approved selling total with expected cost and FX provenance. Flag negative, below-policy, missing-cost, or stale-FX margins without inventing a threshold.
8. Produce one atomic approval packet containing the intended QBO objects, mappings, idempotency key, source IDs, and expected Command Center mirror update.

## Write sequence

Only after exact approval:

1. Recheck duplicates and source version.
2. Create or reuse the QBO customer.
3. Create the approved QBO invoice with the idempotency/request identifier.
4. Capture returned QBO IDs, timestamps, sync token/version, status, and balance.
5. Read the QBO record back.
6. Update the Command Center mapping/mirror only with the verified QBO response.
7. Write an audit record. Stop on partial failure and report the recovery state; never retry blindly.

## Output

Return `READY FOR APPROVAL`, `BLOCKED`, or `EXECUTED AND VERIFIED`, followed by the source summary, validation issues, proposed records, reconciliation checks, approvals required, and verified IDs when execution was authorized.
