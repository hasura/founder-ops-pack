---
name: meeting-prep-brief
description: Build a pre-meeting brief the way a chief of staff would - external meetings only, every source pulled, ending in memory updates and follow-ups, never just a summary. Use before any external call, or as a daily morning review of yesterday's meetings.
---

# Meeting Prep Brief

Prep and review for external meetings, run as a system instead of a scramble.
Sanitized from a production automation that has reviewed every external meeting
daily at 7:00 AM for months, plus its companion per-call brief pipeline.

## The rules that make this work

1. **External-only filter.** Internal-only meetings are noise - skip any meeting
   where every attendee shares your email domain. Review time is a budget; spend
   all of it on outsiders. If you have more than 5 external meetings in the window,
   brief the top 5 by account value and list the rest as one-liners.
2. **A brief pulls from at least 4 sources or it isn't a brief.** For each meeting:
   (a) the call transcript or recording notes if it happened, (b) email threads
   with these attendees from the last 30 days, (c) the account's memory page
   (CRM record, account doc, wiki page - wherever your durable memory lives),
   (d) your own notes/todos mentioning the attendees. Fewer than 4 available?
   Say which are missing at the top of the brief - a gap you can see is safe,
   a gap you can't is how deals die.
3. **Similar-accounts retrieval.** Every brief includes 2-3 accounts that resemble
   this one (same industry, same size band, or same stage) and what happened there.
   A call contextualized against history beats a call summarized in isolation.
4. **The brief ends in writes, not reads.** Last section is always: proposed
   updates to the account memory + follow-up reminders with owners and dates.
   A brief that doesn't end in memory updates is a summary, and summaries rot.

## If/then routing

- If the meeting happened and no transcript exists after 2 hours -> check your
  recorder's fallback order (native recording -> calendar-attached notes -> ask
  the attendee who took notes). Note "no transcript" explicitly; never reconstruct
  from memory as if quoted.
- If an attendee's email domain doesn't match the account -> check whether they're
  a known contact under a personal email before treating them as a new stakeholder.
- If the same account appears in 2+ meetings in one window -> merge into a single
  account-level brief with per-meeting sections.
- If prep surfaces an unanswered question from the LAST meeting -> it goes at the
  top of the new brief, flagged. Unanswered twice = escalate to the account owner.

## Escalation

- Follow-up owed to an external party for 7+ days -> flag in the brief and notify
  the owner directly, not just in the digest.
- Account memory page missing entirely -> create it from the brief's proposed
  updates the same day. Every external account deserves a page after one meeting.

## Worked example

Wednesday 7:00 AM review of Tuesday. Calendar shows 6 meetings; 4 are internal
(all attendees @yourco.com) - skipped. Remaining 2:

**Acme Corp - technical deep-dive (3 external attendees).**
Sources: transcript (48 min), 12 emails over 21 days, account page (last updated
9 days ago), 2 open todos. Similar accounts: BetaCo (same industry, closed-won in
6 weeks after a security review), Gamma Inc (stalled 60 days at the same stage -
stall cause: no economic buyer identified). Brief flags: Acme has no economic
buyer on the page either - same stall pattern as Gamma. Proposed memory updates:
add VP Eng as technical champion (said "I'll take this to our platform review"
at 31:20), log security-review requirement. Follow-ups: send SOC 2 report
(owner: you, due Thu), intro to customer BetaCo reference (owner: AE, due Fri).

**Newlogo Ltd - intro call.** No account page exists -> created from brief.
One follow-up: proposal draft due Monday.

Total review time: 25 minutes for a day with 6 meetings. The filter did that.

## Definition of done

- [ ] Every external meeting in the window has a brief or an explicit one-liner
- [ ] Every brief lists its sources, and missing sources are named
- [ ] Every brief contains at least one proposed memory update
- [ ] Every follow-up has an owner and a date
- [ ] Zero internal-only meetings briefed

## Anti-patterns (each one observed in production before the rule existed)

- **Briefing internal meetings.** The system's first version briefed everything;
  review time tripled and external prep quality dropped. The filter IS the system.
- **The transcript-only brief.** A transcript tells you what was said, not what
  it means for the account. Without the account-memory pull you re-ask questions
  the customer answered two calls ago - the single fastest way to look unprepared.
- **Summaries that end in nothing.** If the last section isn't writes (memory
  updates + follow-ups), the brief gets read and forgotten. Ending in writes is
  what compounds: next meeting's brief pulls the memory THIS brief updated.
- **Reconstructing missing transcripts from memory.** When there is no recording,
  say so. A confident paraphrase presented as record will eventually be quoted
  back to the customer, wrongly.

## Setup (first run, ~30 minutes)

1. Define your external filter: list your internal email domains.
2. Locate your four sources and write down how to query each (recorder,
   email search syntax, where account memory lives, where your notes live).
3. Pick the review slot and put it on the calendar as a recurring block.
4. Do ONE day manually with the template below before automating anything -
   you'll discover which source is unreliable (usually the transcript pipe).
5. Only then automate, keeping the manual template as the output contract.

## Brief template (per meeting)

```
### <Account> - <meeting title> (<date>)
Sources: transcript [ok/missing] | email (N threads) | memory page (updated <date>) | notes (N)
Attendees: <external people + roles, stance if known>
What happened / what's coming: 3-6 bullets, facts with timestamps
Open from last time: <carried-over questions, flagged if unanswered twice>
Similar accounts: <2-3, one line each: what happened there>
PROPOSED MEMORY UPDATES:
- <page/field>: <change> (source: <where>)
FOLLOW-UPS:
- <action> - owner: <who>, due: <date>
```

## Swappable parameters

- Review time: `7:00 AM` daily -> your morning slot
- External filter: email-domain mismatch -> your definition of "outsider"
- Source list: transcript / email / account memory / notes -> your stack's equivalents
- Follow-up staleness: `7 days` -> your tolerance
- Deep-brief cap: `5 meetings` -> your review budget
