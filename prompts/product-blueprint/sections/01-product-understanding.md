# Section 01 — Product Understanding

### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this prompt standalone when you need an exhaustive product analysis before
> committing to architecture or strategy. It goes significantly deeper than the
> master prompt's Section 1.

---

## Inputs

```
PRODUCT_NAME:       [Your product name]
ONE_LINE_PITCH:     [What it does in one sentence]
CORE_PROBLEM:       [The exact problem being solved]
TARGET_USER:        [Primary user — role, industry, daily context]
SECONDARY_USERS:    [Any other user types — admins, viewers, API consumers]
EXISTING_SOLUTION:  [What users do today to solve this problem]
KEY_DIFFERENTIATOR: [What makes your approach fundamentally different]
DOMAIN:             [Industry or domain — healthcare, legal, finance, general, etc.]
```

---

## The Prompt

```
You are a world-class product strategist and UX researcher. Your job is to
produce an exhaustive product understanding document for the product described
below. Be specific, evidence-based, and connect every insight to product
decisions.

INPUTS:
PRODUCT_NAME:       [FILL]
ONE_LINE_PITCH:     [FILL]
CORE_PROBLEM:       [FILL]
TARGET_USER:        [FILL]
SECONDARY_USERS:    [FILL]
EXISTING_SOLUTION:  [FILL]
KEY_DIFFERENTIATOR: [FILL]
DOMAIN:             [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Problem Anatomy

Dissect the core problem into layers:
- **Surface Problem:** What the user says they need.
- **Underlying Problem:** What they actually need (one level deeper).
- **Root Cause:** Why this problem exists structurally.
- **Cost of Inaction:** Quantify what it costs users (time, money, risk) to
  NOT solve this today. Use realistic estimates.
- **Problem Frequency:** How often does this problem occur per user per week?
- **Urgency Triggers:** What events or situations make this problem acute?


## User Persona Deep Dives

For each persona (primary + secondary users):

### Persona: [Name & Role]
- **Profile:** Job title, company size, industry, tech-savviness (1–5).
- **Daily Reality:** Walk through their actual workday. Where does the problem
  appear? (3–4 sentences of narrative.)
- **Top 3 Pain Points:** Specific, not generic. Tied to the product's domain.
- **Current Workaround:** Exactly what tool/process they use today and why it
  fails them.
- **Success Looks Like:** What does their life/work look like AFTER the product
  solves their problem?
- **Buying Behavior:** Who approves the purchase? What triggers a buying
  decision? What creates hesitation?
- **Quote (simulated):** Write a realistic quote this persona might say when
  describing their frustration.


## Jobs-To-Be-Done Analysis

List 5–7 Jobs this product fulfills. For each job use the format:
  "When [situation], I want to [motivation], so I can [expected outcome]."

Then categorize each as:
  - **Functional** (practical task)
  - **Emotional** (feeling/identity)
  - **Social** (perception by others)

Identify which 2–3 jobs are the PRIMARY reasons someone adopts the product vs
the jobs that drive long-term retention.


## Value Proposition Canvas

### Customer Profile
- **Gains:** 5 outcomes the user wants (rank by importance).
- **Pains:** 5 frustrations they experience (rank by severity).
- **Jobs:** Top 3 jobs from the analysis above.

### Product Map
- **Gain Creators:** For each gain, the specific feature that delivers it.
- **Pain Relievers:** For each pain, the specific feature that addresses it.
- **Products & Services:** The core offering and supporting features mapped
  to the jobs.

### Fit Score
Rate the fit (1–10) for each pain/gain pair and explain any gaps that
represent product risk.


## Competitive Moat Analysis

- **Why Now:** What has changed in the market (technology, regulation, behavior)
  that makes this product possible and necessary today?
- **Defensibility:** List 4 moat-building mechanisms available to this product
  (network effects, data flywheel, switching costs, unique integrations, brand).
  For each: how strong is it and how long to build?
- **Category Creation vs Category Entry:** Is this product entering an existing
  category or creating a new one? What are the implications for positioning and
  sales?


## Risk Analysis — Product-Market Fit Risks

List 5 specific risks that could prevent product-market fit:
  - Risk description
  - Leading indicator that warns early
  - Mitigation tactic before and after launch


## Assumption Register

List every major assumption embedded in this product concept:
  - Assumption statement
  - How to validate it (cheapest, fastest method)
  - What you do if it's wrong
```
