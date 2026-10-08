---
name: deferred-revenue
description: Deferred revenue roll-forward and recognition at departure. Use for "deferred revenue", "client deposits", "what can we recognize this month", "departed groups", "restricted funds", "trust shortfall".
---

# Deferred Revenue & Recognition

## Principle
Client money received before departure is a **liability** (Deferred Revenue – Hajj Deposits / Umrah Packages / Tours). It becomes revenue on the **departure/service date**. Matching vendor cost moves from Prepaid (e.g., Prepaid – Amax USA) to COGS on the same date.

## Roll-forward (per line, per month)
```
Opening deferred
+ Deposits received (Airtable PAYMENTS / QBO receipts coded to deferred)
− Released to revenue (bookings with Travel Date in month, status Departed/Completed)
± Refunds / cancellations (no-refund policy — any refund needs Maaz approval note)
= Closing deferred  → must equal QBO liability balance
```

## Steps
1. Pull QBO balances for each deferred revenue account (month start/end).
2. From Airtable `01_BOOKINGS`, list bookings with Travel Date in the month and Total Paid; group by Booking Type.
3. Compute expected release; compare to what QBO actually released. Unreleased departed groups = 🔴 (known: Umrah deferred grew $21K Apr → $707K Sep with no release).
4. Produce a release list for Maaz to approve (departure dates are a Maaz yellow-field input). After approval, the entry is posted by theBPO (or via QBO Advanced revenue recognition schedules if enabled).

## Restricted-fund check
Compare Trust balance + amounts already paid to vendors for future departures vs total deferred revenue. If deferred > (Trust + prepaid vendor), the gap = deposits used as working capital. Report it neutrally with the number and trend; recommend Maaz discuss with the TICO-compliance advisor.

## Output
Roll-forward table by line, release list awaiting approval, gap vs QBO, restricted-fund position.
