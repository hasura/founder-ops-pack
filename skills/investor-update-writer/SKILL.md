---
name: investor-update-writer
description: >
  Write the monthly investor update from one source-of-truth financial
  model: a fixed metrics table, lowlights before highlights, and asks with
  owners and dates. Use when the user asks to draft an investor update,
  a monthly LP or angel update, or asks "what do I tell investors this
  month". Numbers come only from closed months.
license: MIT
metadata:
  version: "1.0"
  tier: M
  provenance: sanitized from the KPI dashboard and board reporting practice of a venture-backed software company
---

# Investor Update Writer

The update is a view of the financial model, not a document with its own
numbers. If a figure in the update cannot be traced to a model cell, it
does not go in the update.

## The fixed metrics table

Pick 6-8 metrics once and report the same ones every month, in the same
order, whether they went up or down:

| Rule | Why |
|---|---|
| Same metrics every month | Rotating metrics reads as hiding something |
| Each metric defined once, in writing | "Active user" drift breaks trend lines |
| Numbers only from closed months | Preliminary numbers get restated, restatements burn trust |
| Show current month, prior month, and 3-month trend | A single number has no direction |
| A definition change gets a change-log line in the update | Silent redefinition is the cardinal sin |

## Cadence and structure

Send within 5 business days of the monthly close. Structure, in order:

1. **One-paragraph summary.** What happened, in numbers.
2. **Lowlights.** First, before highlights. 2-3 items, each with what you
   are doing about it. Investors fund people who see problems early.
3. **Highlights.** 2-3 items, each with a number.
4. **The metrics table.**
5. **Asks.** Each with a specific request, a named person type, and a
   respond-by date. "Let me know if you can help" is not an ask.

## If/then rules

- If the close slips past day 10 → send the update anyway with the prior
  closed month and a one-line note. A late update beats a stale silence.
- If a metric moved more than 20% month-over-month → it gets its own
  sentence explaining why. Never let a reader discover a cliff in a table.
- If you missed last month's update → do not merge two months silently.
  Open with "this covers May and June" and show both columns.
- If an ask got zero responses two months running → cut it or rewrite it.
  A recurring ignored ask trains readers to skim.

## Worked example (real math)

June update, closed July 7. Model shows: MRR $118,400 (May: $104,900),
net revenue retention 96%, burn $210,000, cash $2,940,000.

- MRR grew 12.9% month-over-month. Above the 20% threshold? No. One line
  in the summary, no dedicated paragraph.
- Runway = $2,940,000 / $210,000 = 14.0 months. Last month's update said
  15.2. The delta gets a sentence: burn rose $12,000 from two support hires.
- Lowlight: NRR fell from 101% to 96% on one $4,100/mo churn. The update
  names the churn reason and the fix being shipped, not just the number.
- Definition change this month: "active workspace" now excludes internal
  test accounts. Updating it means updating ALL affected fields together:
  the metric definition doc, the model column, the update's change-log
  line, and the restated prior-month value shown beside the new one. A
  redefined metric with an un-restated trend line is a broken trend line.
- Ask: "Intro to a fintech CFO evaluating usage billing, reply by July 25."

## Validation (definition of done)

- [ ] Every number traces to a model cell from a closed month
- [ ] Same metrics as last month, same order, current + prior + trend shown
- [ ] Lowlights section appears before highlights and names a response to each
- [ ] Every metric moving > 20% has an explaining sentence
- [ ] Every ask has a specific request and a respond-by date
- [ ] Definition changes carry a change-log line and a restated prior value
- [ ] Sent within 5 business days of close, or carries the late-close note

## Adapting this to your company

Swap: the 6-8 metric picks, the 20% explain threshold, the day-5 send
target. Keep: one source-of-truth model, fixed table, lowlights first,
closed months only, and the change-log rule.
