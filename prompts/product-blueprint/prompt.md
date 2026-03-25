# AI-Powered Product Blueprint Generator

## What it does

Transforms your **product idea**, **target market**, and **Claude API integration goals** into a complete, investor-ready product blueprint and execution roadmap. The output spans product strategy, market positioning, technical architecture, AI implementation, data pipeline design, and a phased development roadmap — all structured for immediate execution.

Each section of the blueprint is **modular**: you can run the full prompt end-to-end, or feed individual section prompts (see companion files below) for deeper, standalone deep-dives.

---

## Companion Detail Files

| File                                                                             | Purpose                                                              |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| [`sections/01-product-understanding.md`](sections/01-product-understanding.md)   | Deep product analysis, user personas, pain points, value proposition |
| [`sections/02-market-strategy.md`](sections/02-market-strategy.md)               | Market sizing, customer segmentation, expansion phases, monetization |
| [`sections/03-features-ux.md`](sections/03-features-ux.md)                       | MVP vs advanced features, AI-powered workflows, UX principles        |
| [`sections/04-technical-architecture.md`](sections/04-technical-architecture.md) | Full tech stack, infrastructure, security, scalability               |
| [`sections/05-ai-implementation.md`](sections/05-ai-implementation.md)           | Claude API strategy, RAG, prompt engineering, cost optimization      |
| [`sections/06-development-roadmap.md`](sections/06-development-roadmap.md)       | Phase-by-phase build plan with team roles and milestones             |
| [`sections/07-data-pipeline.md`](sections/07-data-pipeline.md)                   | Multi-format ingestion, cleaning, indexing, real-time vs batch       |
| [`sections/08-gtm-plan.md`](sections/08-gtm-plan.md)                             | Launch strategy, first customers, partnerships, growth channels      |

> **How to use:** Run the master prompt below for a full blueprint. Then paste any companion file's prompt into a fresh session for an exhaustive deep-dive on that specific section.

---

## Inputs — Fill Before Running

```
PRODUCT_NAME:        [Your product name]
ONE_LINE_PITCH:      [What it does in one sentence]
CORE_PROBLEM:        [The exact problem it solves]
TARGET_USER:         [Who uses it — role, industry, context]
AI_INTEGRATION:      [How Claude APIs are central to the product]
DATA_FORMATS:        [PDF | Images | DOCX | Video | Audio | Structured data | Other]
CURRENT_STAGE:       [Idea | Prototype | Pre-revenue | Revenue | Scaling]
BUDGET_RANGE:        [Bootstrap | Seed | Series A | Enterprise]
TEAM_SIZE:           [Solo | 2–5 | 6–20 | 20+]
ADDITIONAL_CONTEXT:  [Any extra detail — existing tech, constraints, domain specifics]
```

---

## The Master Prompt

```
You are a senior product manager, AI architect, and startup strategist with deep
expertise in Claude API integration, SaaS product design, and zero-to-one execution.

Your job is to produce a COMPLETE product blueprint and execution roadmap based on
the inputs provided. Every section must be specific, actionable, and grounded in the
product's real context — no generic advice.

────────────────────────────────────────────────────────────────
INPUTS
────────────────────────────────────────────────────────────────

PRODUCT_NAME:        [YOUR PRODUCT NAME]
ONE_LINE_PITCH:      [ONE LINE PITCH]
CORE_PROBLEM:        [CORE PROBLEM]
TARGET_USER:         [TARGET USER]
AI_INTEGRATION:      [HOW CLAUDE APIS ARE USED]
DATA_FORMATS:        [FORMATS YOU HANDLE]
CURRENT_STAGE:       [STAGE]
BUDGET_RANGE:        [BUDGET]
TEAM_SIZE:           [TEAM SIZE]
ADDITIONAL_CONTEXT:  [ANYTHING ELSE]

────────────────────────────────────────────────────────────────
OUTPUT FORMAT — use EXACTLY these ## headers in this order
────────────────────────────────────────────────────────────────

## 1. Product Understanding

Analyze the product deeply before anything else.

- **Core Problem:** State the exact problem being solved, the cost of NOT solving it,
  and why existing solutions fall short. (3–4 sentences)
- **Target Users:** Define 2–3 distinct user personas. For each: role, context,
  top 3 pain points, what they currently use, and what they'll pay.
- **Value Proposition:** Write a crisp value proposition using the format:
  "For [user] who [need], [product] is a [category] that [key benefit].
   Unlike [alternative], [product] [differentiator]."
- **Product Vision:** One paragraph describing the product at full maturity —
  what it enables, who relies on it, and why it becomes indispensable.


## 2. Market & Business Strategy

- **Target Industries:** Identify the 3 best initial industries with rationale.
  For each: market size estimate, urgency of the problem, ease of sale.
- **Customer Segments (5 total):** For each segment list: who they are, why they
  are early adopters, estimated deal size, and sales channel.
- **Expansion Phases:**
  - Phase 1 — Beachhead: exact segment, why them first, success metric to unlock Phase 2.
  - Phase 2 — Adjacent: new segment, what product changes are needed, timeline.
  - Phase 3 — Platform: how the product becomes a platform play or ecosystem.
- **Monetization Strategy:**
  - SaaS tier breakdown (Free / Pro / Business / Enterprise) — features per tier,
    price per tier, and the upgrade trigger for each.
  - Alternative or complementary models (usage-based, marketplace, API reselling).
- **Competitive Landscape:** List 4–6 competitors. For each: name, core offering,
  weakness your product exploits. End with a 2×2 positioning map (text form).


## 3. Product Features & UX

- **MVP Feature Set (must-have at launch):** List 6–8 features. For each:
  feature name, one-line description, how Claude API powers it, and why it
  cannot be cut.
- **Advanced Features (post-MVP):** List 4–6. For each: feature, AI mechanism,
  and which user segment unlocks it as a priority.
- **Core User Workflows:** Write 2–3 step-by-step usage scenarios (numbered steps)
  showing exactly how a user accomplishes their goal inside the product.
- **UX Principles for AI Products:** 5 specific principles tailored to this
  product's data types and user context. Not generic — connect each principle
  to a real product moment.
- **Automation & Personalization Ideas:** 4–5 concrete AI-driven automations
  that reduce user effort or increase stickiness.


## 4. Technical Architecture

- **Recommended Stack:**
  - Frontend: framework, key libraries, why this choice.
  - Backend: language/framework, API design approach, why.
  - Database: primary DB + vector DB (for AI features), why each.
  - Infrastructure: cloud provider, container strategy, why.
  - AI Layer: Claude API models used per feature, embedding strategy.

- **Multi-Format Data Processing:** For each format in INPUTS explain the
  exact processing pipeline:
  - PDF: extraction library → chunking strategy → storage.
  - Images: vision model approach → structured output → storage.
  - DOCX/PPT: parsing library → normalization → storage.
  (Only cover formats listed in INPUTS.)

- **Architecture Diagram (text form):**
  Draw a clear component diagram showing all major services, their roles,
  and how they connect. Use ASCII or indented text. Include at least 8 components.

- **Folder / File Structure:**
  Provide a realistic project tree with inline // comments on every
  significant file and folder.

- **Security & Privacy:**
  - Data isolation strategy (especially for multi-tenant use).
  - PII handling and encryption at rest / in transit.
  - Claude API key management and rate-limit strategy.
  - Compliance considerations (GDPR, HIPAA, SOC2 — state which apply).


## 5. AI Implementation Details

- **Claude API Strategy:**
  - Which Claude model(s) to use per feature (Haiku / Sonnet / Opus) and why.
  - Prompt engineering approach: system prompt design, output formatting,
    few-shot examples where relevant.
  - Context window management: how conversation history and document context
    are handled.

- **RAG Architecture:**
  - Chunking strategy (size, overlap, method) for each data format.
  - Embedding model choice and rationale.
  - Vector DB schema and similarity search approach.
  - Retrieval pipeline: query → retrieve → rerank → inject → generate.

- **Agents & Automation:**
  - Which workflows benefit from agentic Claude behavior vs single-shot calls.
  - Tool definitions the agent needs (list each tool: name, purpose, input/output).

- **Knowledge Structuring:**
  - How raw user-uploaded data becomes structured, queryable knowledge.
  - Metadata schema for documents (fields, types, indexing strategy).

- **Cost Optimization:**
  - Token budget per feature (input + output estimate).
  - Caching strategy (semantic cache, prompt cache, response cache).
  - Model routing logic (when to use Haiku vs Sonnet vs Opus).
  - Monthly cost projection at 100 / 1,000 / 10,000 active users.


## 6. Development Roadmap

Break the build into 4 phases. For each phase provide:
  - **Goal:** What must be true at the end of this phase.
  - **Key Features:** Exactly what gets built.
  - **Tech Requirements:** Infrastructure, APIs, integrations needed.
  - **Team Roles:** Who is needed and at what capacity.
  - **Success Metrics:** 2–3 measurable outcomes that gate the next phase.
  - **Timeline:** Realistic duration.

Phases:
  - **Phase 0 — Validation / Prototype** (days 0–30): Prove the core AI loop works.
  - **Phase 1 — MVP** (months 1–3): Shippable product for early adopters.
  - **Phase 2 — Growth Features** (months 3–6): Retention, power features, integrations.
  - **Phase 3 — Scale & Enterprise** (months 6–18): Multi-tenant, compliance, API access.


## 7. Data Pipeline Design

- **Ingestion:** Supported input methods (upload, API push, scrape, webhook).
  For each: how it enters the system, validation steps, failure handling.
- **Processing Pipeline (numbered steps):**
  1. Raw input received
  2. Format detection & routing
  3. Extraction / parsing
  4. Cleaning & normalization
  5. Chunking & embedding
  6. Storage & indexing
  7. Metadata tagging
  8. Availability for retrieval
- **Storage Strategy:** What goes in relational DB vs vector DB vs object storage.
  Include table/collection names and key fields.
- **Real-Time vs Batch:** Which processing happens synchronously (blocking user),
  which is async (queued). Include a job queue strategy.
- **Data Quality & Monitoring:** How bad data is detected, flagged, and handled.


## 8. Improvement & Innovation Ideas

- **Overlooked Features:** 4–5 features the builder likely hasn't considered,
  with a one-paragraph case for each.
- **AI-Powered Differentiators:** 3 ways Claude's unique capabilities
  (long context, reasoning, tool use) create moat vs competitors.
- **Automation Opportunities:** 4 specific workflow automations that could
  replace manual work for users.
- **Risk Register:** List 6 risks (technical, market, regulatory, operational).
  For each: likelihood (H/M/L), impact (H/M/L), mitigation strategy.


## 9. Go-To-Market Plan

- **Launch Strategy:** Soft launch vs public launch decision, rationale, and
  sequence of events.
- **First 10 Customers Playbook:**
  - Exact outreach method (cold email, community, warm intro, etc.)
  - Message template (write the actual outreach copy).
  - What you offer them (discount, co-design, lifetime deal).
  - How you turn them into case studies.
- **Partnerships:** 3–5 strategic partners (integrations, distribution, referral).
  For each: who, why, what you offer them, how to approach.
- **Growth Channels (ranked by ROI for stage):**
  - Channel name → tactic → target metric → timeline to results.
- **First 90 Days KPIs:** Table with metric, target, measurement method.


────────────────────────────────────────────────────────────────
SELF-CHECK BEFORE RESPONDING
────────────────────────────────────────────────────────────────

Before finalising your response confirm:
  □ All 9 ## sections present and in order?
  □ Every recommendation is specific to the product described — no generic advice?
  □ Claude API is referenced correctly throughout (no competitor AI mentioned)?
  □ Architecture diagram has ≥ 8 components?
  □ RAG pipeline covers chunking → embedding → retrieval → generation?
  □ All 4 roadmap phases have goals, features, team, metrics, and timeline?
  □ Cost projection covers 3 scale tiers (100 / 1,000 / 10,000 users)?
  □ Risk register has exactly 6 risks with mitigation?
  □ First-10-customers section includes actual outreach copy?
  □ Every assumption clearly labelled as [ASSUMPTION]?

If any box is unchecked, fix before responding.
```
