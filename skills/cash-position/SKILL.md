---
name: cash-position
description: Produce a verified current-cash and short-horizon liquidity brief. Use for cash position, available cash, affordability, runway, funding gaps, or a 14/30/60/90-day forecast. Do not treat QuickBooks book cash alone as verified bank cash.
example-prompt: Show verified unrestricted cash, protected funds, committed outflows, and the first forecast buffer breach.
---

# Cash Position

## Outcome

Give the CEO and controller one defensible liquidity view without double-counting obligations or presenting accounting balances as available cash.

## Source contract

- Bank evidence owns actual cleared cash.
- QuickBooks owns book cash, posted liabilities, and recorded transactions.
- Command Center owns operational collection schedules and supplier commitments.
- Approved payroll, tax, debt, and minimum-buffer policies own their respective forecast assumptions.
- A mismatch becomes an exception; never silently override one source with another.

If bank evidence is missing or stale, label current cash `UNVERIFIED` and provide only a provisional movement forecast. Do not issue a cash-safety verdict.

## Definitions

- **Unrestricted cash:** verified cleared bank cash available for ordinary operations.
- **Restricted or protected cash:** customer funds, trust amounts, taxes, or other balances that policy or contract prevents AMAX from spending.
- **Committed outflows:** approved obligations with an amount and expected payment date.
- **Expected inflows:** probability-adjusted collections with an evidence-backed date.
- **Available after commitments:** unrestricted cash minus deduplicated committed outflows due in the selected horizon.
- **Buffer headroom:** forecast closing unrestricted cash minus the approved minimum cash buffer.

Deferred revenue is a liability and risk signal. Do not subtract it again when its related supplier obligation is already included in committed outflows.

## Procedure

1. Confirm the `as_of` timestamp, entities, currencies, bank evidence freshness, and forecast horizon.
2. Reconcile each verified bank balance to its QuickBooks book balance. Put timing differences and unexplained differences in separate queues.
3. Separate unrestricted, restricted, and unknown-purpose cash. Never assume an unknown balance is spendable.
4. Collect posted liabilities and operational commitments. Deduplicate them using stable booking, bill, vendor, amount, currency, and service-date references.
5. Build base and downside forecasts by dated inflow and outflow. Keep probability assumptions visible.
6. Identify the first date the approved buffer is breached and the transactions driving the breach.
7. Recommend ranked actions such as accelerate a named collection, defer a non-critical payment with approval, or obtain missing bank evidence.

## Required output

- `as_of`, evidence freshness, entity, currency, and confidence.
- Verified bank cash, QuickBooks book cash, and reconciliation difference.
- Unrestricted, protected, and unknown-purpose cash.
- Available after commitments and buffer headroom.
- 14/30/60/90-day base and downside closing cash.
- First buffer-breach date and top drivers.
- Exception queue with owner, evidence needed, and next action.

## Approval boundary

Never move money, pay a bill, use protected funds, alter a forecast assumption, or present financing as committed without explicit authorization from the appropriate finance owner.
