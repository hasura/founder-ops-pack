---
name: decision-memo
description: >
  Write a one-page decision memo: the decision as a question, a named owner,
  costed options, a recommendation, a reversibility class, and a decide-by
  date. Use when the user asks to document a decision, compare options,
  resolve a disagreement, or asks "should we do X or Y". Disputes route to
  the memo owner for arbitration, never to an unrecorded compromise.
license: MIT
metadata:
  version: "1.0"
  tier: M
  provenance: sanitized from the product decision log of a venture-backed software company
---

# Decision Memo

One page, one owner, one date. A decision that lives in a meeting recap is
not a decision. It is a rumor with attendees.

## Required fields

| Field | Rule |
|---|---|
| Decision (as a question) | "Should we X?" Not a topic. A topic cannot be decided |
| Owner | One name. The owner decides after input, no committee |
| Decide-by date | A real date. Cost of delay stated next to it |
| Options | 2-4, each with a dollar or time cost and one risk |
| Recommendation | The owner's pick, in one sentence, before the meeting |
| Reversibility | Type 1 (one-way door) or Type 2 (reversible) |
| Dissent | Recorded by name. Silence in the memo means agreement |

## Reversibility classes

- **Type 2 (reversible):** decide inside 3 business days with whoever is in
  the room. A wrong Type 2 call costs a revert, not an apology tour.
- **Type 1 (one-way door):** contracts over 12 months, anything touching
  customer data, pricing changes, senior hires. Gets the full memo, a
  48-hour comment window, and the owner sleeps on it once.

## If/then rules

- If a decision has no owner after one ask → it escalates to the requester's
  manager the same day. Unowned decisions rot into defaults.
- If the decide-by date passes undecided → the memo auto-flips to "decided
  by default" naming the default outcome and its cost. Deciding late IS a
  decision, record it as one.
- If two people dispute a recorded decision later → route to the memo owner
  for arbitration. The outcome is either an upheld note or a new reversal
  memo. Never an unrecorded compromise.
- If an option's cost is "hard to estimate" → estimate it anyway with a
  stated confidence. A range beats a shrug.

## Worked example (real math)

Question: "Should we build usage-based invoicing or buy a billing vendor?"
Owner: head of product. Decide by: March 14 (each week of delay defers
$8,000/mo of usage revenue we cannot bill).

- Option A, build: 2 engineers x 6 weeks = 12 eng-weeks, ~$34,600 at
  $150K loaded cost. Risk: invoicing edge cases eat a 13th week.
- Option B, buy: $24,000/yr plus 0.5% of billed volume. At $160K/mo billed,
  that is $9,600/yr of volume fees, $33,600/yr total. Risk: migration lock-in,
  Type 1 on a 12-month contract.
- Recommendation: buy. Year-one costs are within $1,000 of each other and
  buying returns 12 eng-weeks to the roadmap.
- Recording the decision: update ALL affected fields together. The memo
  status flips to Decided, the decision log gains the entry with owner and
  date, the roadmap removes the 12 eng-week line, the vendor line lands in
  the budget at $33,600, and the dissent field records the platform lead's
  build preference by name. A memo marked Decided while the roadmap still
  shows the build item produces two truths, which is zero truths.

## Escalation

Arbitration requests go to the memo owner within 1 business day. If the
owner has left the company, ownership passes to their manager, recorded as
a field change with a date, not a silent edit.

## Validation (definition of done)

- [ ] The decision is phrased as a question with a named owner and a decide-by date
- [ ] Every option carries a cost figure and one named risk
- [ ] Reversibility class assigned; Type 1 memos had a 48-hour comment window
- [ ] Dissent recorded by name or explicitly marked "none raised"
- [ ] On decide: memo status, decision log, budget, and roadmap updated together
- [ ] No decision older than its decide-by date without a "decided by default" note

## Adapting this to your company

Swap: the 3-day Type 2 window, the 48-hour comment window, the Type 1
trigger list. Keep: one owner, phrased as a question, costed options,
owner arbitration, and the decided-by-default rule.
