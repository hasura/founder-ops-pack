---
name: inbox-triage
description: >
  Run the inbox in two timed passes a day with four moves and an explicit
  exclusion list. Use when the user asks to triage email, get to inbox
  zero, stop living in the inbox, or set up an email workflow.
license: MIT
metadata:
  version: "1.0"
  tier: S
  provenance: sanitized from the daily channel-scan discipline of a venture-backed software company
---

# Inbox Triage

Two passes a day, 15 minutes each. The inbox is a triage queue, not a
workplace. Work happens on the task ledger.

## The exclusion list (build this first)

The secret is what never enters triage. Auto-filter before the pass:
newsletters, CC-only threads, tool notifications, receipts. Target: the
filtered set is 40-60% of daily volume. Review the filters monthly, not
per-message.

## The four moves

Every remaining message gets exactly one move:

1. **Reply now** if it takes under 2 minutes.
2. **Delegate** with a named owner and a date, then archive.
3. **Defer** onto the task ledger with a date, then archive. The task
   ledger is the source of truth, not the starred pile.
4. **Archive.** The default. Archiving is reversible, ignoring is not.

## If/then rules

- If a pass exceeds 15 minutes → stop, note the count remaining, tighten
  the exclusion filters the same day.
- If the same sender needs a reply 3 days running → schedule a call and
  archive the thread. Chains of 10 short emails are a meeting in disguise.
- If a message sits unmoved through 2 passes → it is a defer you are
  avoiding. Ledger it with a date or archive it.

## Worked example (real math)

Morning pass: 34 messages after filters (68 arrived, 34 filtered, exactly
50%). Moves: 6 replied in under 2 minutes, 3 delegated with owners and
dates, 4 deferred to the ledger with dates, 21 archived. Pass took 12
minutes. Deferring the vendor-quote message means updating ALL affected
fields together: the ledger entry with its date, the owner field, and the
archived thread label linking back. A defer without a ledger date is an
archive wearing a costume.

## Validation (definition of done)

- [ ] Exclusion filters catch 40-60% of daily volume
- [ ] Both daily passes finished inside 15 minutes
- [ ] Inbox empty after each pass; every defer has a ledger entry with a date
- [ ] No message survived 2 passes unmoved

## Adapting this to your company

Swap: pass times, the 15-minute cap, the 2-minute reply bar. Keep: the
exclusion list, exactly one move per message, and the ledger as the only
place work waits.
