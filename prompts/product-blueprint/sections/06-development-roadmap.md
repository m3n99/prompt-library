# Section 06 — Development Roadmap
### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this standalone when planning sprints, hiring, or presenting a build
> plan to investors or co-founders. Outputs a phase-by-phase execution plan
> with team structure, milestones, and risk flags.

---

## Inputs

```
PRODUCT_NAME:        [Your product name]
MVP_FEATURES:        [Paste Section 03 MVP feature list OR summarize here]
TECH_STACK:          [Paste Section 04 stack decisions OR summarize here]
TEAM_SIZE:           [Solo | 2–5 | 6–20 | 20+]
TEAM_SKILLS:         [e.g. 1 full-stack JS, 1 ML engineer, 1 designer]
BUDGET_RANGE:        [Bootstrap | Seed | Series A]
REVENUE_TARGET_Y1:   [e.g. $100K ARR]
MUST_LAUNCH_BY:      [Hard deadline if any, or "flexible"]
```

---

## The Prompt

```
You are an engineering lead and startup CTO. Produce a detailed, realistic
development roadmap for the product below. Prioritize ruthlessly — the goal
is the fastest path to validated revenue, not the most complete product.

INPUTS:
PRODUCT_NAME:        [FILL]
MVP_FEATURES:        [FILL]
TECH_STACK:          [FILL]
TEAM_SIZE:           [FILL]
TEAM_SKILLS:         [FILL]
BUDGET_RANGE:        [FILL]
REVENUE_TARGET_Y1:   [FILL]
MUST_LAUNCH_BY:      [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Phase 0 — Validation & Prototype (Days 0–21)

**Goal:** Prove the core AI loop works end-to-end with real data before
writing production code.

- **Spike deliverable:** What the prototype does (no UI, no auth, no infra
  — just the AI pipeline working).
- **Build list (ordered):**
  1. [Task] — [hours estimate] — [who builds it]
  2. ...
- **Validation criteria:** The 3 specific outcomes that prove the idea works.
- **Kill criteria:** What would make you pivot or stop at this phase.
- **Tools to use:** Fastest way to get to a testable prototype (notebooks,
  scripts, no-code tools, etc.).
- **People to show it to:** Exactly who and how (cold outreach template included).


## Phase 1 — MVP (Weeks 3–12)

**Goal:** A shippable product that early adopters will pay for.

### Sprint Plan
Break into 3-week sprints. For each sprint:
  - Sprint goal (one sentence)
  - Feature tickets (name + brief description + story points)
  - Definition of done
  - What gets demoed to users at sprint end

### Technical Foundation
What must be built before features (auth, DB, CI/CD, Claude API client,
file upload pipeline). Order of operations.

### Team Structure
| Role | Responsibilities | FT/PT | Week hired (if not day 1) |
|---|---|---|---|

### MVP Success Metrics (gate to Phase 2)
  - Metric 1: [what, target number, by when]
  - Metric 2: [what, target number, by when]
  - Metric 3: [what, target number, by when]

### MVP Risk Register
  - Top 5 risks with probability, impact, and mitigation.


## Phase 2 — Growth Features (Months 3–6)

**Goal:** Drive retention and expand to new customer segments.

- **Feature additions (prioritized list):** For each: name, which segment it
  unlocks, Claude API mechanism, estimated build time.
- **Integrations to build:** Which third-party integrations drive the most
  growth. Build vs buy decision for each.
- **Infrastructure upgrades:** What breaks at 10x Phase 1 scale and when to
  fix it.
- **Team additions:** What roles are needed and what triggers the hire.
- **Revenue target:** Specific ARR goal and the customer mix to achieve it.


## Phase 3 — Scale & Enterprise (Months 6–18)

**Goal:** Enterprise readiness, platform expansion, and repeatable growth.

- **Enterprise requirements:** SSO, audit logs, SLA, custom contracts, dedicated
  support — which are needed and in what order.
- **Compliance:** Which certifications to pursue, timeline, cost estimate.
- **API / Platform play:** Should the product expose its own API? Under what
  conditions? What does the developer ecosystem look like?
- **Org structure at this phase:** Engineering, product, sales, CS, ops roles
  needed.
- **Infrastructure at scale:** Multi-region, DR, 99.9% uptime SLA requirements.


## Dependency Map

List all external dependencies that could block progress:
| Dependency | Type | Risk Level | Mitigation |
|---|---|---|---|
| Claude API rate limits | External API | Medium | Request limit increase early |
| ... | ... | ... | ... |


## Technical Debt Tracker

List the deliberate shortcuts taken in Phase 0–1 that must be fixed before
Phase 3:
| Shortcut | Why taken | When to fix | Cost to fix later |
|---|---|---|---|


## Definition of Done — Checklist

For every feature before it ships, confirm:
  □ Unit tests written and passing
  □ Claude API prompt tested with edge case inputs
  □ Error states handled in UI
  □ Loading and empty states implemented
  □ Mobile-responsive (if web)
  □ Logged to observability stack
  □ Reviewed by at least one other person
  □ Deployed to staging and smoke-tested
  □ Rollback plan documented
  □ User-facing copy reviewed
```
