# Section 03 — Product Features & UX

### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this standalone when designing the product's feature set, user flows,
> and AI interaction patterns. Especially useful before writing any specs or
> starting UI design.

---

## Inputs

```
PRODUCT_NAME:       [Your product name]
PRODUCT_CONTEXT:    [Paste Section 01 output OR summarize in 5–8 sentences]
PRIMARY_PERSONA:    [Name and role of main user]
DATA_FORMATS:       [PDF | Images | DOCX | Text | Structured data | Other]
AI_CAPABILITIES:    [Which Claude capabilities are central — summarization |
                     extraction | generation | reasoning | agents | vision]
PLATFORM:           [Web app | Mobile | Desktop | API | All]
```

---

## The Prompt

```
You are a senior product designer and AI product specialist. Produce a complete
feature set, UX strategy, and AI interaction design for the product below.
Be specific — name real UI components, flows, and Claude API techniques.

INPUTS:
PRODUCT_NAME:       [FILL]
PRODUCT_CONTEXT:    [FILL]
PRIMARY_PERSONA:    [FILL]
DATA_FORMATS:       [FILL]
AI_CAPABILITIES:    [FILL]
PLATFORM:           [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Feature Prioritization Framework

Before listing features, apply this lens to every candidate feature:
  - **Impact:** How directly does it solve the core problem? (H/M/L)
  - **Effort:** Engineering complexity (H/M/L)
  - **AI Leverage:** Does Claude make it meaningfully better? (H/M/L)
  - **Retention Driver:** Does removing it cause churn? (Y/N)

Use this to sort features into: Must-Have | Should-Have | Nice-to-Have | Never-MVP.


## MVP Feature Set

List exactly 6–8 features that ship at launch. For each:

### Feature: [Name]
- **What it does:** One clear sentence.
- **User story:** "As a [persona], I want to [action] so that [outcome]."
- **Claude API role:** Which model, what prompt type, what the output looks like.
- **Input:** What data the user provides or the system fetches.
- **Output:** What the user sees/gets.
- **Why it cannot be cut:** The specific consequence of launching without it.
- **Acceptance criteria:** 3 testable conditions that define "done."


## Post-MVP Feature Roadmap

List 4–6 features for Phase 2+. For each:
  - Feature name and description
  - Which user segment drives the most demand for it
  - Claude API mechanism that powers it
  - What MVP usage data would justify building it


## Core User Workflows

Write 2–3 detailed workflows. For each workflow:

### Workflow: [Goal the user is trying to achieve]
**Trigger:** What causes the user to start this workflow?

Step-by-step (numbered):
  1. [What user does] → [What the system does] → [What Claude does behind the scenes]
  2. ...
  (Continue until goal is achieved or the workflow ends with an output)

**Happy path:** The ideal no-friction version.
**Edge cases:** 2–3 things that can go wrong and how the product handles them.
**Time to value:** How long does this workflow take from start to meaningful output?


## AI Interaction Design Principles

List 5 UX principles specific to this product's AI features:

### Principle: [Name]
- **What it means for this product:** One concrete sentence.
- **Product moment it applies to:** The specific UI/UX situation.
- **Implementation example:** What the UI actually shows or does.
- **Anti-pattern to avoid:** The common mistake this principle prevents.


## AI Transparency & Trust

Users need to trust AI outputs. Define:
- **Confidence signals:** How the product communicates certainty vs uncertainty.
- **Source attribution:** How Claude's outputs are traced back to source data.
- **Human override points:** Where users can correct, edit, or reject AI output.
- **Error states:** What the UI shows when Claude fails, times out, or returns
  low-quality output.
- **Explainability:** For complex AI outputs, how is the reasoning surfaced?


## Personalization & Automation

List 4–5 AI-driven personalizations or automations. For each:
  - What behavior it adapts or automates
  - The signal/data used to trigger it
  - How Claude produces the personalized output
  - How users control or opt out
  - The measurable impact on retention or engagement


## Accessibility & Inclusion

For each DATA_FORMAT in INPUTS, address:
  - How users with visual/motor/cognitive limitations interact with this feature
  - Fallback experiences when AI processing fails
  - Language and localization considerations


## Notification & Engagement Design

- Define the 5 most important notification types (in-app, email, push).
- For each: trigger, message, CTA, and the user behavior it drives.
- Anti-patterns: 3 notification mistakes to explicitly avoid.
```
