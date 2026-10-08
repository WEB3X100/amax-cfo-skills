---
name: booking-to-books
description: Turn a new or changed booking into the right financial records. Use for "new Hajj/Umrah/tour booking", "set up payment schedule", "create invoice for booking", "add customer to QuickBooks", "sync booking to QBO".
---

# Booking → Payment Schedule → Vendor Obligations → QBO

## 1. Check the booking (CRM / `01_BOOKINGS`)
Required before anything financial: Customer, Booking Type, Package, Travel Date, Pax, Total Invoice Amount, Total Cost (Vendor), Distributor (if any). If missing, list what's missing and stop.

## 2. Proposed payment schedule (`10_PAYMENT SCHEDULE`)
| Type | Schedule |
|---|---|
| Hajj | $3,000/person deposit at booking (June) → monthly instalments on the 15th (Jun–Nov) → final balance 1 month before departure |
| Umrah | 50% at booking (locks flights) → balance 30+ days before departure (funds hotel/transport/visa) |
| Tour | 20–30% deposit → balance 30–45 days before departure |
| Air ticket | 100% before issuance |

## 3. Proposed vendor obligations (`11_VENDOR OBLIGATIONS`)
| Type | Obligation |
|---|---|
| Hajj | Amax USA monthly deposits Jun–Nov; flights before travel |
| Umrah | Airline at booking; Amax USA hotel+transport+visa 30 days before departure |
| Tour | Vendors 30–60 days before departure |

## 4. QBO
- Search customer; if none, propose creating it (name, email, phone only).
- Propose invoice: product mapped to the right revenue line, Class = line, service date = departure date. Deposits post to Deferred Revenue.
- Optional payment link.

## Approval
Show all proposed rows/records in one summary. Write nothing until Maaz or Sara replies "approve". After writing, report the IDs created.

## Margin sanity
If Margin % < 8% (Umrah/Hajj) or negative, flag 🔴 before approval. If priced in USD cost with CAD sale, show FX assumption.
