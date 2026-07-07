---
name: deal-memory
description: A 6-page opportunity memory structure that keeps deal state durable, auditable, and agent-maintainable - MEDDPICC, contacts, value case, action plan, competition, timeline. Use when setting up deal tracking or upgrading a CRM full of stale free-text notes.
---

# Deal Memory

The memory schema that turns "notes about a deal" into deal state you can
trust. Sanitized from a production system where AI agents maintain opportunity
memory across email, calls, and chat - the structure is what makes that safe.

## The 6-page structure

Every opportunity gets exactly six pages. Not one page with six headings -
six pages, because they update at different tempos and from different sources.

1. **Qualification (MEDDPICC)** - one section per letter, each holding evidence
   with dates, not adjectives. "Champion: VP Eng, said 'I'll drive this' on
   May 12 call" - not "strong champion".
2. **Contacts** - every person touched, with role, stance (champion / neutral /
   blocker / unknown), and last-contact date.
3. **Value Case** - the customer's numbers in the customer's words: current cost,
   target state, quantified delta. If this page is empty at Proposal stage,
   that's your at-risk signal regardless of activity.
4. **Action Plan** - dated steps to close, each with an owner ON BOTH SIDES.
   A plan with only your names on it is a wish.
5. **Competition** - who else is in, their angle, your counter, evidence.
6. **Timeline** - append-only dated log of every material event. Timeline is
   DATA: one line per event, `date | source | event`, machine-parseable.

## Formatting rules live IN the memory

The top of each page states its own formatting rules (2-3 lines). Anyone -
human or agent - editing the page reads the rules at the moment of writing.
Rules that live in a separate style guide do not survive contact with editors.

## If/then

- If new information contradicts a page -> the page updates AND the timeline
  logs the change with its source. Correction without a log line is how
  memories silently rot; the log line without the correction is half a fix.
  Both, always.
- If a MEDDPICC section has no evidence newer than 30 days -> mark it STALE
  inline. Stale evidence reads as no evidence in deal reviews.
- If a contact goes 21+ days without touch at Negotiation stage or later ->
  Action Plan gets a re-engage step, auto-dated.
- If the Value Case is still empty when the deal enters Proposal -> block the
  proposal send until you can fill at least "current cost" and "target state".

## Escalation

- Two consecutive deal reviews where the same page is stale -> the deal owner
  presents that page (not the whole deal) at the next review.
- Economic Buyer unidentified past Discovery -> flag on Qualification page;
  this is the single most predictive stall factor.

## Worked example

Acme, $120K ARR opportunity. Monday call transcript lands. Updates:
Qualification: Decision Criteria gains "must pass platform security review"
(source: call, May 12, 31:20). Contacts: adds Priya (Platform Lead, stance
unknown, last contact May 12). Action Plan: "security docs to Priya - you,
May 14 / review scheduled - Priya (their side), May 20". Timeline appends:
`2026-05-12 | call | Security review is gating; Priya owns it`.
Wednesday: an email shows procurement wants Net-60 vs your Net-30. Value Case
unchanged; Timeline appends the ask; Competition unchanged; Qualification's
Paper Process section updates with the terms conflict + date. Five minutes of
edits, and the Friday deal review needs zero verbal download - the pages ARE
the review.

## Definition of done

- [ ] All 6 pages exist from Discovery onward (empty sections marked, not absent)
- [ ] Every MEDDPICC claim carries a source and a date
- [ ] Every Action Plan step has an owner on the correct side and a date
- [ ] Timeline is append-only, one `date | source | event` line per event
- [ ] Any page edit that changes a fact has a matching timeline line

## Anti-patterns

- **One page with six headings.** The pages update at different tempos from
  different sources; merging them means every edit scrolls past everything,
  and agents editing "the deal doc" clobber each other. Six pages, six tempos.
- **Adjective evidence.** "Strong champion" survives every review unchallenged.
  "Said 'I'll drive this' on May 12" can be checked, aged, and marked stale.
  If a claim has no date, it's a mood.
- **Free-text timelines.** Prose timelines can't be queried, diffed, or fed to
  an agent. `date | source | event` - the discipline costs three characters
  of pipe per line and pays forever.
- **Correcting the page without logging, or logging without correcting.** Both
  halves or neither is trustworthy. A page that silently changed can't be
  audited; a log entry pointing at a wrong page actively misleads.

## Setup (per deal, ~15 minutes at Discovery)

1. Create the six pages from the templates below. Empty sections stay,
   marked `(no evidence yet)` - absence of a section hides the gap.
2. Paste the 2-3 formatting rules at the top of each page.
3. Backfill Timeline from whatever exists (emails, first call). Even three
   lines of history beats a timeline that starts mid-deal.
4. Book the deal-review slot; the pages are the agenda from day one.

## Page skeletons

```
QUALIFICATION: one section per MEDDPICC letter -> evidence lines: <claim> (source, date)
CONTACTS: table -> name | role | stance | last contact | notes
VALUE CASE: current cost | target state | quantified delta | in whose words
ACTION PLAN: table -> step | owner (side) | due | status
COMPETITION: table -> competitor | their angle | our counter | evidence
TIMELINE: append-only -> date | source | event
```

## Working with agents

This structure is what makes agent-maintained deal memory safe: the routing
is deterministic (see companion skill `call-to-memory`), edits are auditable
(timeline), and staleness is visible (dates on everything). If you let an
agent maintain these pages, give it the formatting rules as system context
and grant it append-only rights on Timeline - corrections to past timeline
lines are human-only.

## Swappable parameters

- Qualification framework: MEDDPICC -> BANT / SPICED / your methodology
- Staleness: `30 days` evidence, `21 days` contact-touch -> your cycle length
- Value Case gate at Proposal -> your stage names
- Storage: wiki pages -> CRM objects / Notion / docs folder (structure survives all)
