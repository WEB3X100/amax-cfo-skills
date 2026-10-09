---
name: bookkeeping-close
description: Control an evidence-backed month-end close, expose blockers, and measure time to a trusted finance-owner sign-off. Use for close status, close checklist, uncategorized balances, reconciliation coverage, controller review, or readiness for financial reporting.
example-prompt: Give me the month-end close status, unresolved controls, owners, and the shortest path to a trusted sign-off.
---

# Bookkeeping close control

## Outcome

Help the controller close one accounting period from an approved cutoff to a trusted sign-off without recreating QBO financial statements in the bot.

## Start conditions

Confirm the entity, period, QBO close calendar, controller, approved materiality/tolerance, source cutoff, and required classes/departments. If the close calendar or tolerance is unavailable, mark it missing rather than hard-coding a target.

## Control sequence

1. **Source completeness:** statements/evidence received; bank and card feeds current; all operational invoice, bill, payment, and booking cutoffs recorded.
2. **Subledger integrity:** A/R and A/P reviewed; received payments applied; vendor bills entered; Command Center operational records mapped to QBO or placed in the exception queue.
3. **Cash:** every bank, card, trust/restricted, and clearing account reconciled to independent evidence.
4. **Revenue:** deferred-revenue roll-forward tied to QBO; recognition events supported by approved service evidence; refunds/cancellations reviewed.
5. **Costs:** supplier bills, COGS, prepaids, accruals, FX, taxes, and commissions reviewed under controller policy.
6. **Classification:** uncategorized, suspense, opening-equity, deleted/inactive-account, missing class/department, and intercompany/shareholder items cleared or explicitly accepted.
7. **Analytical review:** P&L and balance sheet by approved dimensions; material month-over-month or budget variances explained.
8. **Sign-off:** controller evidence attached, open exceptions accepted or resolved, QBO period closed/locked by an authorized human.

## Status model

For each control report `NOT STARTED`, `IN PROGRESS`, `BLOCKED`, `READY FOR REVIEW`, or `SIGNED OFF`. Calculate completion only from required controls with evidence; a missing source is not complete. Show reporting currency and do not combine currencies without approved conversion.

## Output

- Period, cutoff, days elapsed, evidence freshness, and overall close state.
- Control table: control, status, owner, evidence, exception amount/count, next action, due date.
- Material exception queue ranked by financial impact and reporting risk.
- Today list: who must do what next.
- Sign-off packet: reconciled totals, accepted exceptions, controller/approver, timestamp, and QBO close/lock evidence.

## Boundary

The bot may analyze and draft. Posting adjustments, accepting exceptions, closing/locking a period, or distributing financial statements requires exact authorized approval. Never call a close trusted until all required controls have evidence or the controller has explicitly accepted the named exceptions.
