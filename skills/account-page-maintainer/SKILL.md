---
name: account-page-maintainer
description: Keep an agent-maintained account plan trustworthy - 8-section schema, conservative evidence-based qualification grading out of 80, never-delete rules for mutual action plans, and row-level audit timestamps. Use for strategic accounts where the plan must survive scrutiny.
---

# Account Page Maintainer

Account-plan upkeep with the validator discipline that makes agent-maintained
documents trustworthy. Sanitized from a production system that maintains
graded account pages for strategic deals.

## The 8-section account schema

1. **Header** - account, segment, owner, ARR (current/target), next milestone + date.
2. **Qualification scorecard** - graded, see below.
3. **Stakeholder map** - table: name | role | stance | influence (H/M/L) | last touch.
4. **Mutual Action Plan (MAP)** - dated steps, owners on both sides. Governed by
   the never-delete rule below.
5. **Value case** - customer's numbers, customer's words.
6. **Competition & risks** - live list with evidence.
7. **History digest** - rolling summary of material events (feeds from timeline).
8. **Audit block** - see row-level timestamps below.

## Conservative grading: 0-10 per letter, /80 total

Each qualification dimension (MEDDPICC = 8 letters) scores 0-10, summing to /80.
The grading rule that matters: **scores are awarded on written evidence, and
ties break DOWN.** No evidence = 0, not 5. A verbal "sounds good" is a 3, not
a 7. Score inflation is the death of account reviews - a /80 that reads 61
should feel EARNED. Calibration anchor points:

- 0-2: nothing, or hearsay
- 3-5: verbal signals, single-threaded, undated or aging evidence
- 6-8: written/confirmed evidence, current (<30 days), multi-threaded
- 9-10: contractual/structural proof (signed MAP step, budget line confirmed in writing)

## The MAP never-delete rule

MAP steps are never deleted. Completed -> checked with completion date.
Abandoned -> ~~struck through~~ with one-line reason and date. The MAP is a
negotiation record: a customer who watched three steps silently vanish stops
trusting the document, and so should you. Strike-throughs are FEATURES - the
pattern of what got abandoned tells you how the deal is really going.

## Row-level audit timestamps

Every row/line that carries a fact ends with `[src: <source>, <date>]`.
Not per-page "last updated" - per row. When an agent maintains the page,
this is the difference between reviewable and hopeful: any human can pick
any row and check it in under a minute.

## If/then

- If a score changes by 3+ points in one update -> the edit must cite the
  specific evidence; the audit block logs old score, new score, evidence.
- If any letter scores 0 past Discovery stage -> that letter becomes a MAP step
  ("identify economic buyer" is a step with an owner and a date, not a hope).
- If a stakeholder's last touch exceeds 21 days and influence is H -> re-engage
  step auto-added to MAP.
- If the agent proposes an edit it can't attach a source to -> the edit is
  rejected as a matter of process, even if it's probably right. "Probably
  right without a source" is exactly the rot vector.

## Escalation

- Total score DROPS week-over-week during an active evaluation -> account owner
  notified same day with the specific rows that moved; falling scores mid-cycle
  are the earliest churn/loss signal this system produces.
- Two strike-throughs on customer-side MAP steps within 30 days -> escalate to
  deal review: the customer is quietly deprioritizing.

## Worked example

Acme, week 6. Agent processes Thursday's call. Proposed edits: Decision
Criteria 4 -> 7 (written security requirements received [src: email, Jun 3]);
Champion stays 5 despite enthusiastic call - no written action taken (ties
break down); MAP: "platform review" struck through - postponed by customer,
reason logged [src: call, Jun 3] - second customer-side strike this month ->
escalation fires. New total: 51/80 (was 49; up on paper). Deal review reads
the two strike-throughs against the +2 and correctly reads the deal as
COOLING despite the rising score. The strike-through pattern caught what the
number missed - that's the schema working.

## Definition of done

- [ ] All 8 sections present; empty ones marked, not removed
- [ ] Every score justified by written evidence at the anchor-point level
- [ ] Zero deleted MAP rows (checked or struck through only)
- [ ] Every fact row carries `[src, date]`
- [ ] Score changes of 3+ logged with before/after and evidence
- [ ] The page passes the 1-minute test: any row, verifiable in 60 seconds

## Anti-patterns

- **Score inflation to keep reviews pleasant.** A page full of 7s that never
  moves teaches everyone to ignore the number. Conservative grading makes the
  score MEAN something - a 61/80 you can defend beats a 70 you can't.
- **Deleting abandoned MAP steps to "clean up".** The deletions are the data.
  A clean-looking MAP with invisible churn is a lie the document tells you.
- **Page-level "last updated" instead of row-level sources.** "Updated
  yesterday" tells you nothing about WHICH facts are current. Rot hides in
  aggregate freshness.
- **Letting the agent grade.** Agents propose evidence and draft edits; the
  score change is applied by a human against the anchor points. Grading is
  judgment; judgment stays with the accountable owner.

## Setup (per account, ~30 minutes)

1. Create the 8 sections; fill Header and whatever Stakeholders/History exist.
2. Grade the scorecard cold, from written evidence only. Expect a shockingly
   low first score - that's calibration working, not failure.
3. Draft the MAP with the customer ON A CALL - a MAP written unilaterally is
   section 4 theater. Even 3 mutual steps beats 10 of yours.
4. Wire the maintenance loop: what feeds it (calls, email - see
   `call-to-memory`), who approves edits, when reviews happen.

## Review protocol (weekly, 10 minutes per strategic account)

Read ONLY: the audit block (what changed), score deltas with evidence,
strike-throughs since last week, and stakeholders past touch threshold.
Do not re-read the whole page - the schema exists precisely so review
attention goes to deltas. Monthly, do one full-page read to catch drift
the deltas hide.

## Swappable parameters

- Framework: MEDDPICC/80 -> BANT/40, SPICED/60 - keep 0-10 per dimension
- Evidence freshness: `30 days` -> your cycle
- Re-engage trigger: `21 days` for H-influence -> your tempo
- Grading anchors -> tune wording, keep ties-break-down
