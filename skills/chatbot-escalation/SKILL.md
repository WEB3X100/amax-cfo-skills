---
name: chatbot-escalation
description: Handle payment and finance questions escalated from the customer chatbot. Use when a message is tagged from the chatbot, or for "customer asking about balance", "client wants refund", "client says they paid".
---

# Chatbot Escalations (finance)

The customer-facing chatbot routes finance questions here. I prepare the answer for **staff**; I don't reply to the customer directly unless an admin has enabled auto-reply for that intent.

## Intents
| Intent | What I do |
|---|---|
| "What's my balance?" | Look up client in CRM → booking → `10_PAYMENT SCHEDULE`. Draft reply with next due date + amount + how to pay. Verify identity first (booking reference + phone/email on file). |
| "I already paid" | Search `12_PAYMENTS`, QBO receipts, and recent bank feed for amount ±$5 and date ±5 days. If found → draft confirmation and flag "apply payment in QBO" to Sara. If not → ask staff to request proof of payment. |
| Refund / cancellation | Policy is **no refund** on Hajj/Umrah once vendor commitments are made. Draft a polite policy-based reply and escalate to Maaz. Never promise money back. |
| Payment plan / extension | Show current schedule, vendor deadline that depends on it, and risk. Recommend options; Maaz decides. |
| Invoice copy / receipt | Find in QBO; draft reply with document for staff to send. |

## Rules
- Identity check before sharing any balance.
- Never share another traveller's info in a group booking unless the requester is the group lead on file.
- Log the interaction to `23_COMMUNICATIONS LOG` (Channel = Chatbot) once staff confirm.
