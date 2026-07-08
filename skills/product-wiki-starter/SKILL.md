---
name: product-wiki-starter
description: >
  Start and maintain a product wiki: pages for what your product/services
  are, what your data means, and — the part everyone skips — the design
  decisions and their WHY. Use when the same product question gets asked
  twice, when a new hire asks "why is it built this way?", or when giving
  an AI agent product context. Trigger keywords: why did we, design
  decision, decision log, how does our product, what does this field mean,
  product documentation.
---

# Product Wiki Starter

Product knowledge decays in a specific order: first the WHY disappears,
then the WHAT gets re-asked, then someone re-litigates a decision that
was settled two years ago — and either wastes a week reaching the same
conclusion or, worse, un-makes a decision whose constraints still hold.
A product wiki's job is to stop that decay, and the WHY is the part
worth the most.

Three page types:

## 1. Concept pages — one per term

One page per product concept, feature, or term your team actually says
out loud ("workspace", "the sync job", "credits"). Each page: what it is
in two lines, how it behaves at the edges, and what it is often confused
with. If a term means two things (a "project" to sales vs. a "project"
in the codebase), the page says so explicitly — terminology collisions
are the #1 source of cross-team miscommunication and the cheapest to fix.

## 2. Data pages — one per dataset or metric surface

What each table/dataset/export actually contains, which fields are
trustworthy vs. legacy, and the known traps ("`status=active` includes
suspended accounts; filter on `suspended_at IS NULL` too"). Every trap
someone discovers goes on the page the same day — the second person to
hit a data trap that the first person already found is pure process
failure.

## 3. Decision log — the thesis of this skill

One dated entry per significant design decision, in this exact shape:

- **Decision:** one sentence, in the imperative ("Store money as integer
  cents, never floats").
- **Why:** the constraints and alternatives at the time. 3-5 bullets.
  Write the losing options down — "we chose X" is half a decision;
  "we chose X over Y because Z" is the whole one.
- **Expires when:** the condition under which this should be revisited
  ("if we ever bill in currencies without minor units", "when we pass
  10K daily jobs"). Most decisions are contingent, not eternal; recording
  the contingency is what separates a decision log from a rulebook.

The discipline: **an entry is written within a week of the decision, by
someone who was in the room.** A decision log reconstructed later is
historical fiction — better than nothing, but label it as such.

**Disputed decisions get an arbiter, not a debate thread.** Every
decision-log entry names one owner (the person who was in the room and
wrote it down). When a recorded decision is disputed — someone believes
the WHY no longer holds, or that it never did — the entry's owner
arbitrates: they hear the challenge, check it against the recorded
constraints and the "expires when" condition, and either uphold the entry
or write the reversal as a new entry. If the owner has left, the current
area owner inherits the entry. One named arbiter per entry is what keeps
a disputed decision from becoming a recurring meeting; this is the same
rule that keeps a metric dictionary from having two definitions of
revenue.

## Worked example

A new engineer proposes moving job scheduling from a cron table to a
queue. The decision log has a 14-month-old entry: "Decision: cron table,
not a queue. Why: at <2K jobs/day the queue adds an infra dependency for
no throughput gain; ops burden of the queue was the deciding factor over
elegance. Expires when: sustained >10K jobs/day or multi-region." Current
volume: 40K/day. The entry doesn't say "no" — it says the decision was
contingent and its expiry condition has been met. The proposal goes
through in one meeting, with the original constraints as the starting
point instead of an archaeology project. Time saved is real (a week of
re-derivation), but the bigger win is the opposite case it prevents:
re-making the move at 1K jobs/day, when the original WHY still held.

## Maintenance discipline

- Concept and data pages: fix-on-touch. Whoever finds a page wrong or
  stale fixes it in the same sitting (under 5 minutes) or files it with
  an owner (over 5).
- Decision log: append-only, one owner per entry, written within a week.
  Reversals get a NEW entry referencing the old one — never edit history.
  Disputes route to the entry's owner for arbitration (see above); the
  outcome is either "upheld, here's why the constraints still hold" or a
  new reversal entry — never an unrecorded compromise.
- Quarterly, scan decision-log entries whose "expires when" conditions
  reference numbers you now exceed. Each hit is a scheduled revisit, not
  an automatic reversal.

## Using it with AI agents

This is the context that stops an AI agent from confidently proposing
something your team already rejected for reasons that still hold. Plain
markdown, one folder: concepts/, data/, decisions/. Works as repo docs a
coding agent reads, Claude Project knowledge, Notion, any harness.

## Validation

- Every term used in your last all-hands product update has a concept page.
- Every data trap discovered in the last quarter appears on a data page
  (check against your support/eng chat — traps discussed but not recorded
  are the failure mode).
- Decision log entries all have the three fields; >80% written within a
  week of the decision; every entry has an "expires when", even if it's
  "probably never — record why".
- Every decision-log entry has a named owner who is still at the company
  (or an explicit inheritor); any dispute in the last quarter ended in an
  upheld note or a new entry, not an unresolved thread.
- The decision-log test: hand a new hire your three most-questioned
  decisions. If the log answers "why is it built this way?" without a
  meeting, it's working.

The 5-minute fix-on-touch rule, one-week write-down window, and quarterly
expiry scan are the defaults; the Decision/Why/Expires-when shape is the
skill.
