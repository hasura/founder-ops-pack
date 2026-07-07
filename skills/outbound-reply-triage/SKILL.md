---
name: outbound-reply-triage
description: The follow-up discipline where outbound actually dies - reply capture on a 2-hour work-hours cadence, a stale-response sweep that catches every dropped thread at 7 days, and weekly reconciliation. Use alongside any outbound motion.
---

# Outbound Reply Triage

SDR management of the reply inbox, sanitized from a production system whose
core insight is that outbound dies not in the sending but in the dropped
follow-up.

## The three loops

**Loop 1 - Reply capture, every 2 hours during work hours.**
Sweep the inbox for replies to sequenced threads. Classify each into exactly
one bucket: positive / referral / objection / not-now / negative / auto-reply.
Route: positive -> book-a-time draft within the same 2-hour window; referral ->
new-thread draft to the referred person (reference the referrer BY NAME);
objection -> tailored draft for human review; not-now -> snooze with a date;
negative -> suppression list + sequence kill; auto-reply (OOO) -> extract the
return date, snooze until return + 1 day.

**Loop 2 - The stale-response sweep (the sauce).**
Daily: find every thread where THEIR last reply is newer than YOUR last reply
and 7+ days have passed. Each hit gets exactly one of two treatments:
an AI-drafted revival for human review, or **mark-dark** (an explicit decision
to let it die, logged with a reason). No third state. The unlogged limbo
thread - too old to be active, too alive to be dead - is where pipeline rots.

**Loop 3 - Weekly ID reconciliation.**
Reconcile message/thread IDs between inbox, sequencer, and your DB. Threads
the sequencer thinks are active but the inbox shows replied = replies your
capture loop missed. Every mismatch is a bug in Loop 1 - find the cause
(usually: reply from a different address than the one sequenced).

## If/then

- If a positive reply sits unanswered past ONE capture window -> escalate to
  owner's direct attention; positive-reply response time is the highest-leverage
  metric in outbound.
- If the same objection appears 3+ times in a week -> it's not an objection,
  it's a positioning gap. Feed it back to whoever owns messaging, with quotes.
- If a revival draft gets no response in 10 days -> mark-dark automatically;
  one revival per thread, ever. Two revivals reads as desperation.
- If someone replies to a DEAD thread (marked-dark or completed) -> highest
  priority bucket of all; dormant-thread revivals close at the highest rate
  of any reply type.

## Escalation

- Loop 3 finds >5% ID mismatch two weeks running -> capture pipeline is
  structurally broken; fix before sending another batch.
- A negative reply mentions legal/spam/unsubscribe language -> same-day
  suppression at the DOMAIN level + notify the outbound owner.

## Worked example

Tuesday. 10 AM capture: 6 replies. 1 positive (demo request - draft ready
10:40, sent by human 11:15); 1 referral ("talk to our platform lead" -> new
draft referencing referrer); 2 OOO (return dates extracted: snoozed to Jul 14,
Jul 21); 1 objection ("we built this in-house" - 3rd time this month -> quote
logged to positioning doc AND tailored draft queued); 1 negative -> suppressed.
Stale sweep: 4 hits. Thread A (their reply 9 days old, deal-adjacent):
revival drafted. Threads B, C (11 and 13 days, low-fit segment): mark-dark,
reason "segment deprioritized Jul batch". Thread D: 8 days, engaged-no-reply
history -> revival. Friday reconciliation: 2 mismatches of 214 threads (0.9%)
- both replies from personal addresses; capture query widened to match on
name+domain. Nothing in limbo. That's the whole system.

## Definition of done

- [ ] Every reply bucketed and routed within one 2-hour window
- [ ] Stale sweep ran; every 7+ day thread is revival-drafted OR marked-dark with reason
- [ ] Zero limbo threads (their-reply-newer, no decision)
- [ ] Weekly reconciliation done; every mismatch root-caused
- [ ] Recurring objections (3+/week) fed back with quotes

## Anti-patterns

- **Triage as inbox-checking.** "I watch the inbox" is not a capture loop.
  Without the 2-hour cadence and the bucket taxonomy, positive replies age
  into cold ones - response time is the metric prospects actually feel.
- **The limbo pile.** Threads nobody replied to and nobody killed. Limbo feels
  like optionality; it's actually a graveyard with better marketing. The
  two-treatment rule (revive or mark-dark) exists to make the decision
  unavoidable.
- **Serial revivals.** If one revival didn't land, the second one won't either
  - it just converts "no answer" into "actively avoiding". One revival,
  then dark.
- **Treating OOO as a reply.** It's a snooze instruction with a date in it.
  Parse the date; touching them mid-vacation wastes the touch.

## Setup (first run, ~45 minutes)

1. Define the six buckets in writing with one example reply each - the
   taxonomy only works if two people (or you and an agent) bucket the same
   reply the same way.
2. Wire the capture query: all replies to sequenced threads, matching on
   thread ID AND sender name+domain (personal-address replies are the #1
   miss - see the worked example).
3. Build the stale-sweep query: their-last-reply > my-last-reply AND
   age >= 7 days.
4. Create the mark-dark log (thread, date, reason). The reason field is
   load-bearing: quarterly, the reasons tell you which segments to stop
   sequencing at all.
5. If an agent runs the loops: agent buckets, drafts, and sweeps; a human
   approves objection drafts and all revival sends for the first two weeks.
   The bucket taxonomy + the two-treatment rule are a definition of done the
   agent can self-grade against - that's what makes this delegation safe.

## Swappable parameters

- Capture cadence: `2 hours` work-hours -> your reply-time bar
- Stale threshold: `7 days` -> your market's tempo
- Revival policy: `1 per thread, 10-day timeout` -> your persistence bar
- Objection-pattern trigger: `3/week` -> your volume
