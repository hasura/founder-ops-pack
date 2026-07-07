---
name: team-wiki-starter
description: >
  Start and maintain a team wiki: one page per person covering what they own,
  what they care about, and how they like to work — so anyone (human or AI
  agent) can route work to the right person without asking around. Use when
  onboarding someone, when "who owns this?" takes more than one message to
  answer, or when giving an AI agent context about your team. Trigger
  keywords: who owns, who should I ask, team directory, working with me,
  onboarding doc, people context.
---

# Team Wiki Starter

Every team above ~5 people pays a routing tax: "who owns billing?" gets
asked in chat, answered by whoever's online, and asked again next month.
The org chart doesn't answer it — ownership lives one level below titles.
A team wiki is one page per person that makes routing instant, for humans
and for AI agents working on your team's behalf.

The rule that makes this work: **a person's page is what the rest of the
team needs to know to work with them — not their bio.** Résumé facts go
unused; routing facts get used weekly.

## The page template

One page per person, four sections, in this order:

1. **Owns** — the systems, processes, accounts, and decisions this person
   is the single owner of. Each item is a noun someone would search for
   ("invoicing", "the staging environment", "the Acme account"), not a
   duty statement. If two pages claim the same noun, that's a real
   ownership conflict the wiki just surfaced — resolve it, don't soften it.
2. **Cares about** — their active priorities this quarter and the 2-3
   standing things they always want to hear about. This is what turns an
   FYI into a correctly-targeted FYI.
3. **Working preferences** — channel (async doc vs. call), response-time
   expectations, meeting hours, timezone, and the escalation path: how to
   reach them urgently, and what qualifies as urgent (name a dollar or
   customer-impact threshold, e.g. "call me for anything customer-visible
   or >$5K").
4. **Route to them for** — a literal list of question patterns they are
   the right first stop for. Write it in other people's words, not theirs:
   "my expense report is stuck" routes to finance ops even though finance
   ops would never phrase it that way.

Keep each page under 40 lines. Longer means it's become a bio again.

## Maintenance discipline

A stale team wiki is worse than none — people trust it, route wrong, and
then stop trusting all of it. Three rules keep it alive:

- **Ownership changes update the page in the same message.** The handoff
  isn't done until both pages (old owner, new owner) reflect it. Same
  discipline as a code review: the change and its documentation ship
  together.
- **Every page carries a last-verified date.** Anything older than 90
  days is flagged stale at the top of the page. Verification is the page
  owner re-reading their own page — 3 minutes a quarter.
- **New hires write their own page in week 1** from the template, and
  their onboarding buddy reviews it. Writing "route to me for" forces the
  exact conversation about scope that onboarding usually leaves implicit.

## Worked example

A 12-person startup, before: "who can approve a $3K conference sponsorship?"
produced a 9-message chat thread ending in "probably Dana?". After the
wiki: Dana's page, **Owns** section, lists "discretionary spend approvals
up to $10K"; her **Working preferences** section says "async by default,
Slack DM for anything time-boxed under 24h". The question became one
lookup and one correctly-shaped DM. Multiply by the ~15 routing questions
a week a 12-person team generates: at even 10 minutes saved each, that's
~2.5 hours/week the wiki returns — and the errors it prevents (asking the
wrong person, who answers anyway) are worth more than the time.

## Using it with AI agents

This structure is exactly the context an AI agent needs to draft messages,
route requests, and decide who to loop in. Keep the wiki as plain markdown
files (one per person) and it works as: a folder any coding agent can
read, project knowledge in a Claude Project, pages in Notion, or context
in any agent harness. The format is the product; the tool is
interchangeable.

## Validation

- Every page has all four sections and is under 40 lines.
- No noun appears in two people's **Owns** sections (run this check
  quarterly; conflicts are findings, not errors).
- Every page has a last-verified date newer than 90 days.
- The test that matters: pick last week's three "who owns…?" questions
  from chat. If the wiki answers all three in one lookup, it's working.
  If it answered zero, the pages are bios — rewrite the **Owns** and
  **Route to them for** sections first.

All numbers here (40 lines, 90 days, $5K urgency threshold) are defaults
that work at 5-50 people — swap them to your context, but keep them
explicit.
