---
name: prd-one-pager
description: >
  Write a one-page PRD: the user problem with evidence, the smallest
  shippable cut, explicit non-goals, and a pre-registered success metric.
  Use when the user asks to write a PRD or product spec, scope a feature,
  or asks "what are we actually building and why".
license: MIT
metadata:
  version: "1.0"
  tier: M
  provenance: sanitized from the product decision log and customer-voice practice of a venture-backed software company
---

# PRD One-Pager

One page is a forcing function, not a formatting preference. A PRD that
needs ten pages is hiding an undecided decision on nine of them.

## Required sections

| Section | Rule |
|---|---|
| Problem | Whose problem, with evidence: quote count, ticket count, or revenue at stake. Verbatim quotes beat summaries |
| Evidence | Account-weighted. Five requests from one account is one account's problem |
| Smallest shippable cut | What ships first that a real user can use. Not phase 1 of 3, a complete small thing |
| Non-goals | Explicit list of what this does NOT do, with one line why. The non-goals section prevents three roadmap fights |
| Success metric | Pre-registered: metric, baseline, target, and the date it gets read. Defined in the metric dictionary before build starts |
| Open decisions | Each with an owner and a decide-by date, per the decision-memo discipline |

## The pre-registration rule

The success metric and its read date are written before the build
starts. Deciding after launch which number to look at is how every
feature becomes a success. If the metric needs new instrumentation,
that instrumentation is part of the smallest shippable cut.

## If/then rules

- If the problem section has no verbatim customer evidence → the PRD is
  a hypothesis doc; label it as one and downgrade the build commitment
  to a spike.
- If the smallest cut takes more than one cycle → it is not the smallest
  cut. Cut again, and move the remainder to non-goals-for-now.
- If a stakeholder disputes a shipped scope decision → route to the PRD's
  decision log entry and its named owner, never relitigate from memory.
- If the read date arrives and the metric missed → the PRD gets a dated
  outcome note either way. PRDs without outcome notes teach the next
  PRD nothing.

## Worked example (real math)

Problem: enterprise admins cannot audit who exported data. Evidence: 7
requests across 4 accounts (account-weighted: 4 votes, not 7), one
churned account named it in the exit call, $86,000 ARR at stake across
the 4. Smallest cut: an export-events log page, filterable by user and
date. Non-goals: real-time alerts, SIEM integration, retention policies
(one line each). Success metric, pre-registered: "audit-page weekly
active admin accounts, baseline 0, target 12 of the 31 enterprise
accounts by day 45", defined in the dictionary before build. At day 45
the read shows 9 of 31. The outcome note records the miss, and writing
it means updating ALL affected fields together: the PRD's outcome note,
the metric-dictionary entry gaining the actual, the follow-up decision
memo ("alerts next, or stop here") with its owner and decide-by date,
and the roadmap line. A missed metric without a follow-up decision is a
number nobody agreed to act on.

## Escalation

Scope disputes route to the open-decision owner. Evidence disputes (is
this real demand?) route to the evidence table: more accounts or a
spike, decided by the PRD owner within one week, in writing.

## Validation (definition of done)

- [ ] Fits on one page
- [ ] Problem carries verbatim, account-weighted evidence with a dollar or count figure
- [ ] Smallest cut is one cycle and independently usable
- [ ] Non-goals listed with reasons
- [ ] Success metric pre-registered with baseline, target, read date, dictionary entry
- [ ] Read date honored with a dated outcome note and a follow-up decision

## Adapting this to your company

Swap: the one-cycle bar, the read-date offset, section names. Keep:
account-weighted evidence, smallest-shippable-cut discipline, explicit
non-goals, and pre-registered metrics with outcome notes.
