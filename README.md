# AMAX CFO Skills

Portable finance procedures for the AMAX CFO bot. Every skill is a standard Agent Skills folder containing one `SKILL.md`, so the repository can be imported by OpenBot and other compatible agent hosts.

The pack contains procedures only. It must not contain client records, balances, account suffixes, credentials, tokens, connection strings, private contact details, or production exports.

## Import

In the bot's Skills screen, import:

```text
WEB3X100/amax-cfo-skills
```

Review the ten detected skills and enable only the procedures the bot needs. Importing a skill supplies instructions; it does not install a QBO, bank, CRM, or Command Center connection and does not grant write authority.

## System-of-record contract

All skills follow the same source hierarchy:

1. **QuickBooks Online (QBO)** owns posted accounting customers and vendors, invoices, bills, payments, journal entries, account balances, classes/departments, and financial reports.
2. **AMAX Command Center/Postgres** owns operational quotes, bookings, fulfillment, payment schedules, workflow exceptions, QBO mappings, and mirrored QBO status. It is not a second general ledger.
3. **Twenty CRM** owns pre-sale people, relationships, opportunities, owners, stages, and follow-up context.
4. **Bank evidence** owns actual cleared cash and statement ending balances.
5. **Approved migration evidence** may explain historical conversion, but a workbook or legacy system must not become a parallel live ledger.

When sources disagree, the bot creates an exception. It must never silently overwrite one source with another or present an unreconciled number as trusted.

## Operating contract

- Default to read-only analysis and draft preparation.
- Separate observed facts, calculations, assumptions, and recommendations.
- Show source, as-of time, freshness, currency, exclusions, and reconciliation status for every material number.
- Treat unavailable data as unavailable, never as zero.
- Keep booked sales, invoiced amounts, cash collected, deferred revenue, and recognized revenue separate.
- Keep currencies separate unless an approved FX rate and rate date are shown.
- Require exact human approval immediately before any QBO write, payment action, external message, CRM change, or Command Center mutation.
- After an approved write, verify the returned system ID and read the record back before reporting success.
- Minimize personal data. Never expose passport data, dates of birth, payment instruments, credentials, or another traveller's information.

## Skills

| Skill | Use it for |
| --- | --- |
| `ar-collections` | Prioritized receivables and staff-approved collection drafts |
| `booking-to-books` | Validating a booking and preparing an idempotent QBO posting packet |
| `bookkeeping-close` | Evidence-backed month-end close control |
| `cash-position` | Verified unrestricted cash and short-horizon liquidity |
| `chatbot-escalation` | Staff-only drafts for customer finance questions |
| `deferred-revenue` | Deferred-revenue roll-forward and recognition exceptions |
| `distributor-settlement` | Partner settlement calculations and exception packets |
| `investigate` | Narrow ad-hoc finance investigations when no specialist skill fits |
| `qbo-reconcile` | Bank/card reconciliation preparation and unmatched-item queues |
| `vendor-deadlines` | Supplier commitments, AP deadlines, and funding risk |

## OpenBot compatibility

Each `SKILL.md` uses:

- a folder-matching `name`;
- a discriminating `description`;
- an optional `example-prompt` for the OpenBot preview;
- concise procedures and explicit verification/approval boundaries.

The pack is intentionally dependency-free. Skills may use connectors already configured for the bot, but they must fail closed when a required source is unavailable.

## Change control

The pre-optimization baseline is Git commit `75ecfc9`. This revision is a governed candidate until representative, edge, and dangerous canaries confirm correct routing, source attribution, abstention, approval handling, and no critical safety regression.
