---
name: ar-collections
description: Prioritize receivables, reconcile customer balances, and prepare staff-reviewed collection actions. Use for who owes us, overdue invoices, AR aging, collection risk, payment recovery, or reminder drafts. Do not use for supplier bills or bank reconciliation.
example-prompt: Show the overdue receivables that need action this week and explain any balance mismatches before drafting reminders.
---

# A/R collections control

## Outcome

Give finance a source-backed collection queue that targets the right payer without chasing cash already received or exposing unnecessary personal data.

## Sources and trust

1. Use QBO A/R Aging Summary and Detail for posted open receivables.
2. Use Command Center invoice/payment schedules, booking, travel date, payer type, owner, and QBO mapping for operational context.
3. Use Twenty only for relationship owner and approved contact context.
4. Use verified bank evidence only to identify a probable received-but-unapplied payment.

If QBO and the operational schedule disagree, open an exception. Do not change either source or accuse the customer.

## Procedure

1. Confirm the as-of date, entity, currency, and scope. Record source timestamps.
2. Exclude voided, deleted, disputed, or already-settled items only when the authoritative source proves that state.
3. Reconcile each material balance by QBO invoice ID, Command Center invoice/booking ID, payer, currency, original amount, applied payments, and open balance.
4. Classify mismatches: received/unapplied, missing QBO invoice, duplicate, currency/FX, wrong customer, timing, disputed, or unknown.
5. Prioritize only reconciled or explicitly caveated items using amount, days overdue, days to service, customer promise date, last staff contact, and relationship owner.
6. Route distributor/partner-booked balances to the contractually responsible payer; never assume the traveller owes the balance.
7. Draft a collection action with owner, channel, tone, due date, evidence, and the next escalation point. Use the approved contract and policy; never invent penalties, release consequences, or incentives.

## Output

- Headline: reconciled overdue total, number of payers, near-service exposure, and exception amount.
- Priority table: payer, document/booking reference, currency, open amount, aging bucket, service date, promise/last contact, owner, reconciliation status, next action.
- Exception queue with mismatch type and evidence needed.
- Staff-only message drafts where requested.
- Up to three owner-assigned actions.

## Approval and verification

Drafting needs no external-action approval. Sending a reminder, generating a payment link, changing an invoice, or logging a customer-facing communication requires exact approval for the recipient, document, amount, channel, and text. After any approved mutation, verify the returned record ID/status before reporting completion.
