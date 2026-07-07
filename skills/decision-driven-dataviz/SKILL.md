---
name: decision-driven-dataviz
description: >
  Build charts and dashboards where every chart answers a named decision,
  with opinionated defaults that prevent the standard failure modes. Use
  when creating any chart, reviewing a dashboard, or deciding whether a
  visualization should exist at all. Trigger keywords: dashboard, chart,
  visualization, graph this, KPI display, reporting view.
---

# Decision-Driven Dataviz

Most dashboards are answers to "what data do we have?" The useful ones
are answers to "what decision does someone make while looking at this?"
That single reframe kills most chart-junk before it's built.

## The rule

**Every chart carries a named decision.** Before building, complete this
sentence: "Someone looking at this decides whether to ____." If you
can't, the chart is decoration — cut it or demote it to an appendix. A
dashboard is a list of decisions, rendered.

Corollary: the decision names the audience, and the audience sets the
grain. "Decide whether to page someone" wants a 5-minute grain; "decide
whether to change pricing" wants quarters. A chart serving two decisions
at two grains is two charts.

## Opinionated defaults (break them only with a written reason)

- **No dual axes.** Two axes on one chart lets the eye manufacture
  correlations that scale choice created. Two charts, stacked, sharing
  an x-axis.
- **No 3D, ever.** Depth encodes nothing and distorts everything.
- **Pie charts only for ≤3 slices** that sum to a meaningful whole —
  beyond that, a sorted bar chart. Humans compare lengths well and
  angles badly.
- **Label the takeaway, not the data.** The title is the finding
  ("Churn is concentrated in month-2 self-serve"), not the description
  ("Churn by cohort and plan"). If the takeaway changes when the data
  refreshes, the title is a template with the current finding filled in.
- **Start bar charts at zero.** Truncated bars manufacture drama. Line
  charts may zoom, but say so on the chart.
- **One highlight color.** Everything else is gray. The color budget is
  the editorial voice: spending it everywhere is spending it nowhere.
- **Annotate events on time series** (launch, pricing change, outage).
  A spike without its annotation generates a meeting to rediscover what
  the annotation would have said.

## Worked example

A weekly ops dashboard had 14 charts; the review meeting ran 50 minutes.
Applying the rule: 5 charts had a nameable decision (staffing level,
paging threshold, queue re-prioritization, vendor escalation, weekly
ship/hold), 9 didn't. The 9 moved to a linked appendix. The 5 got
takeaway titles and one highlight color. The meeting dropped to 20
minutes, and the two decisions that had been buried in chart 11 and 13
(both staffing) started actually getting made weekly. Nothing was
deleted — the appendix satisfies "but I sometimes look at it" without
taxing the decision surface.

## Assembling the dashboard

Order charts by decision cadence, not by topic: decisions made daily at
the top, weekly in the middle, quarterly at the bottom (or on a separate
view — mixing cadences trains people to skim past the slow charts, and
then they skim past everything). Each section header names the decision
family, not the data family: "Staffing" not "Ticket volumes". Cap the
main view at 7 charts; the appendix is unlimited but linked, not shown.
And every dashboard carries an owner and a last-reviewed date — an
unowned dashboard reverts to chart-junk within two quarters, one
harmless "can we just add…" at a time.

## Validation

- Every chart on the main view has its decision written in its config
  or doc — spot-check 3 charts by asking their owner "what decision?"
  and expect the same answer that's written down.
- Main view ≤7 charts, ordered by decision cadence, every section
  header naming a decision family.
- Zero dual-axis, zero 3D charts; every pie ≤3 slices.
- Every title states a finding. Read titles alone, top to bottom: they
  should read as this week's briefing.
- The meeting test: if the dashboard review meeting summarizes charts
  instead of making decisions, the dashboard failed this skill —
  re-run the cut.

The defaults are the skill; the ≤3-slice and zero-baseline numbers are
the two you may tune (to ≤5 and "annotated non-zero") if you write down
why.
