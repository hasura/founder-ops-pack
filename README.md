# Founder Ops Pack

**26 skills and 6 agents in the repo today, written from systems we run
daily. 13 curated community skills, vendored with attribution. Growing to
44 skills and 12 agents.**

Most skill packs ship hundreds of bulk-generated entries. We wrote ours by
sanitizing systems we run in production at Hasura. The close runbook is our
close runbook. The task reconciler is the one that runs every morning.
Nothing here was generated from scratch. Each skill keeps the specific
numbers, thresholds, and escalation rules of the original. Swap them for
your own.

Works in Claude Code, Codex, Cursor, PromptQL, Gemini CLI, GitHub Copilot,
and any tool that reads the Agent Skills format. ChatGPT users: `chatgpt/`
has a paste-ready text twin of every skill. Install steps for every tool:
[INSTALL.md](INSTALL.md).

> **Status:** 26 of 44 skills and 6 of 12 agents are in the repo today.
> Everything in the index below ships. If it isn't in `skills/` or
> `agents/` yet, it's days away. Watch the repo.

## What this replaces

A lean team pays six or seven figures a year for the work in this table:

| You currently pay for | Typical cost | Skills / agents in this pack |
|---|---|---|
| SDR / outbound rep | $85K-$120K/yr fully loaded | `cold-email-sequencer`, `outbound-reply-triage`, `outbound-sdr` (agent) |
| Customer success headcount / tooling | $70K-$120K/yr per CSM | `engagement-health-classifier`, `lifecycle-email-orchestrator`, `customer-success-manager` (agent) |
| Bookkeeper / controller / fractional CFO | $3K-$22K/mo | `monthly-close-runbook`, `runway-scenario-model`, `fractional-cfo-lite` (agent) |
| Unmanaged SaaS renewals / seat waste | 10-30% of SaaS spend recoverable | `vendor-stack-audit` |
| Executive assistant / chief of staff | $65K-$125K/yr (or $3K-$7.5K/mo fractional) | `todo-reconciler`, `meeting-prep-brief`, `chief-of-staff` (agent), `executive-assistant` (agent) |
| RevOps / sales ops analyst | $26K-$83K/yr interpretation labor | `deal-memory`, `call-to-memory`, `account-page-maintainer`, `weekly-metrics-digest`, `revops-analyst` (agent) |
| Competitive intel platform + analyst | $15K-$60K/yr + labor | `voice-of-customer-synthesizer` |
| Sales engineering questionnaire time | days per enterprise deal | `rfp-security-questionnaire` |
| Launch / program management | agency retainers | `launch-command-center`, `channel-signal-digest` |

Every skill in the table is sanitized from a system in daily production
use, or seeded from one.

## The full index

Tiers: **L** = flagship (120-180 lines, ships templates in `assets/` where
natural). **M** = standard (80-120 lines, full quality bar). **S** = utility
(40-70 lines, one pattern).

### Skills

| Skill | What it replaces / encodes | Who it's for | Tier | Source |
|---|---|---|---|---|
| `todo-reconciler` | The chief-of-staff-grade task list that stays true to reality | Everyone | L | ours (production) |
| `meeting-prep-brief` | Pre-meeting research an EA or chief of staff does | Everyone | L | ours (production) |
| `channel-signal-digest` | Reading every channel so you don't have to | Everyone | L | ours (production) |
| `deal-memory` | Deal-state tracking a RevOps analyst maintains | Sales / GTM | L | ours (production) |
| `call-to-memory` | Post-call notes that land in durable account memory | Sales / GTM, CS | L | ours (production) |
| `account-page-maintainer` | Account-plan upkeep with graded qualification audits | Sales / GTM | L | ours (production) |
| `cold-email-sequencer` | Outbound sequence writing | Sales / GTM | L | ours (production) |
| `outbound-reply-triage` | SDR management of the reply inbox | Sales / GTM | L | ours (production) |
| `lifecycle-email-orchestrator` | Lifecycle/onboarding email operations (the send-ledger rule) | Founder, CS, growth | L | ours (production) |
| `engagement-health-classifier` | CSM book-of-business health review | Customer success | L | ours (production) |
| `monthly-close-runbook` | Bookkeeper / controller month-end close | Finance | L | ours (production) |
| `weekly-metrics-digest` | Analyst weekly reporting | Founder, RevOps | L | ours (production) |
| `voice-of-customer-synthesizer` | Customer/competitive intel synthesis | Product, GTM | L | ours (production) |
| `launch-command-center` | Launch program management | Anyone launching | L | ours (production) |
| `rfp-security-questionnaire` | Security-questionnaire fire drills | Sales engineering | L | ours (production) |
| **Wiki seeds** (starter pages for the team, customer, and product wikis) |
| `team-wiki-starter` | Tribal knowledge about who does what | Everyone | M | ours (production) |
| `customer-wiki-starter` | Account context living in one seller's head | Founder, sales, CS | M | ours (production) |
| `product-wiki-starter` | Undocumented design decisions and their why | Product, eng | M | ours (production) |
| `metric-dictionary` | The single source of truth for what your numbers mean | Everyone | M | ours (production) |
| `decision-driven-dataviz` | Chart-junk dashboards nobody acts on | Anyone reporting numbers | M | ours (production) |
| `runway-scenario-model` | Fractional-CFO scenario planning: base/bear/bull + pre-committed triggers | Founder, finance | M | ours (production) |
| `vendor-stack-audit` | SaaS renewal calendar, 90/60/30 windows, seat-waste recovery | Founder, ops, finance | M | ours (production) |
| `delegation-brief` | Handoffs (to humans or AI agents) that don't boomerang | Everyone | S | ours (production) |
| **Personal ops** (organize and prepare, never advise) |
| `personal-monthly-close` | Personal-finance chaos | Everyone | S | ours (production) |
| `tax-doc-organizer` | Shoebox of receipts in April | Everyone | S | ours (production) |
| `doctor-visit-prep` | Forgetting your symptoms in the exam room | Everyone | S | ours (production) |

**Coming:**

decision-memo, sop-runbook-writer, investor-update-writer, board-meeting-pack, fundraise-pipeline, okr-quarterly-planning, interview-debrief-scorecard, prd-one-pager, case-study-extractor, inbox-triage, crisp-status-update, weekly-review-reset, feedback-sbi, 1on1-operating-system, new-hire-30-60-90, bug-sev-triage, contract-first-pass, crm-hygiene

If it isn't in skills/ yet, it's days away.

### Agents

Agent playbooks live under `agents/`. Each one orchestrates a set of skills
for a role ("act as my fractional CFO") and carries the same required
sections as a skill: operating rhythm, if/then rules, escalation logic, a
worked example with real math, and a definition of done the agent can grade
itself against.

| Agent | What it replaces | Skills it orchestrates |
|---|---|---|
| `chief-of-staff` | Chief-of-staff judgment support: the ledger, the daily brief | `todo-reconciler`, `meeting-prep-brief`, `channel-signal-digest` |
| `executive-assistant` | EA execution: scheduling, follow-ups, inbox, logistics ($65K-$125K/yr) | `meeting-prep-brief` |
| `outbound-sdr` | SDR seat: sequences, reply triage, the weekly outbound rhythm ($85K-$120K/yr) | `cold-email-sequencer`, `outbound-reply-triage` |
| `customer-success-manager` | CSM monitoring loop: health, lifecycle plays, churn signals | `engagement-health-classifier`, `lifecycle-email-orchestrator` |
| `fractional-cfo-lite` | Fractional CFO core: the close + the runway model ($8K-$22K/mo) | `monthly-close-runbook`, `runway-scenario-model` |
| `revops-analyst` | RevOps analyst: deal memory, pipeline hygiene, the Friday digest | `deal-memory`, `call-to-memory`, `account-page-maintainer`, `weekly-metrics-digest` |

**Coming:**

meeting-copilot, deal-memory-keeper, metric-librarian, board-prep-partner, product-ops-analyst, people-ops-partner

If it isn't in agents/ yet, it's days away.

## Start here, by role

- **Founder** → `todo-reconciler`, `metric-dictionary`.
- **Team of one (founder, consultant, chief of staff)** → `todo-reconciler`
  (start here), `meeting-prep-brief`, `channel-signal-digest`,
  `lifecycle-email-orchestrator`.
- **Sales / GTM** → `deal-memory` + `call-to-memory`, then
  `cold-email-sequencer` + `outbound-reply-triage`.
- **Finance** → `monthly-close-runbook`, then `runway-scenario-model` and `vendor-stack-audit`.
- **Customer success** → `engagement-health-classifier` +
  `lifecycle-email-orchestrator` (mind the send-ledger rule).

## Curated collection

We also vendor 13 community skills from 5 authors. Selection rule: we only
include skills we would run ourselves.

**Licensing protocol:**
- Permissively-licensed skills (MIT, Apache, CC-BY) are vendored into
  `curated/` with the original LICENSE file and an ATTRIBUTION note (author,
  repo, license). These appear in the index below with `Source = curated from
  [author]`.
- Restrictively-licensed or unlicensed skills are never copied. Instead,
  they're linked in [CURATED.md](CURATED.md) with context on why they're worth
  using. The link is the curation.

### What code ships in curated/ (security note)

Exactly one curated skill ships executable code: `brainstorming` (from
obra). Four scripts under `curated/obra/brainstorming/scripts/`
(`helper.js`, `server.cjs`, `start-server.sh`, `stop-server.sh`) run a
local-only web server for its optional visual companion. We read every line
before vendoring. What we verified: zero outbound network calls anywhere;
the server binds `127.0.0.1` by default; file writes are confined to its
own session directory (`/tmp/brainstorm` or an explicit `--project-dir`);
`child_process` is used only to open your browser, opt-in and via `execFile`
(no shell); access is token-gated with owner-only file permissions; and the
stop script refuses to kill processes it can't verify it started. Every
other curated skill is markdown and JSON only, with no executable code.

Read the scripts yourself before running any skill that ships them, here or
anywhere else. When we pull updates from upstream, we re-review the code
before the update lands.

### Curated Skills (Vendored with Attribution)

| Skill | What it replaces / encodes | Who it's for | Tier | Source |
|---|---|---|---|---|
| `seo-audit` | SEO health check with concrete diagnostics | Marketing, growth | curated | curated from coreyhaines31 |
| `pricing` | SaaS pricing strategy (packaging, metrics, tiers) | Founder, product | curated | curated from coreyhaines31 |
| `copywriting` | Conversion copywriting for landing pages | Marketing, growth | curated | curated from coreyhaines31 |
| `cro` | Conversion rate optimization audits | Marketing, growth | curated | curated from coreyhaines31 |
| `runway-calculator` | Startup runway modeling and burn analysis | Founder, finance | curated | curated from iamfiscus |
| `cash-flow-forecast` | Cash flow forecasting discipline | Founder, finance | curated | curated from iamfiscus |
| `client-profitability` | Client/account profitability analysis | Finance, services | curated | curated from iamfiscus |
| `brainstorming` | Structured brainstorming frameworks | Everyone | curated | curated from obra |
| `writing-plans` | Plan-writing discipline for agent work | Everyone | curated | curated from obra |
| `retro` | Team retrospective facilitation | Founder, managers | curated | curated from garrytan |
| `office-hours` | Office hours operating system | Managers, advisors | curated | curated from garrytan |
| `experiment-design-kit` | Growth experiment design with guardrails | Growth, product | curated | curated from gtmagents |
| `launch-tiering` | Product launch tiering framework | Product, GTM | curated | curated from gtmagents |

## Quality bar

Every skill under `skills/` (the ones we wrote) has five required sections:
specific numbers and thresholds, an if/then decision framework, escalation
logic, one worked example with real math, and a validation section the
agent can grade itself against. Utility skills are shorter (40-70 lines)
but still carry a number, a rule, an example, and a validation step. If
anything under `skills/` reads like generic AI advice, file an issue.
That's a bug.

Curated skills are their authors' work. We picked them on the same rule (we
only include what we'd run ourselves) but the authors own the content.
