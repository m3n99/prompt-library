# AI-Powered Product Blueprint Generator

A modular, production-grade prompt system for building complete product blueprints
around Claude API integration. Works for any AI-native SaaS product at any stage.

## How It Works

Run the **master prompt** (`prompt.md`) for a full end-to-end blueprint in one shot.

Then use any **companion file** to go deeper on a specific section — each one is a
standalone prompt with its own inputs and detailed output specification.

## Files

```
product-blueprint/
├── prompt.md                          ← Master prompt (start here)
└── sections/
    ├── 01-product-understanding.md    ← Problem anatomy, personas, JTBD, value prop
    ├── 02-market-strategy.md          ← Sizing, segments, pricing, competitive moat
    ├── 03-features-ux.md              ← MVP features, workflows, AI interaction design
    ├── 04-technical-architecture.md   ← Stack decisions, ADRs, schema, security
    ├── 05-ai-implementation.md        ← Claude API, RAG, agents, cost optimization
    ├── 06-development-roadmap.md      ← Phase-by-phase build plan, sprints, team
    ├── 07-data-pipeline.md            ← Ingestion, extraction, chunking, storage
    └── 08-gtm-plan.md                 ← Launch, first customers, channels, KPIs
```

## Recommended Workflow

```
1.  Fill inputs in prompt.md → run master prompt → get full blueprint
2.  Identify the 2–3 sections most critical for your current stage
3.  Run those companion prompts with the master output as context
4.  Use the deep-dive outputs to write specs, technical docs, or investor materials
```

## Chaining Sections

Companion prompts are designed to accept prior outputs as context:

```
Section 01 output → feeds into → Sections 02, 03, 04, 05, 08
Section 02 output → feeds into → Sections 06, 08
Section 03 output → feeds into → Sections 05, 06
Section 04 output → feeds into → Sections 05, 06, 07
```

Paste the relevant prior output into the `PRODUCT_CONTEXT` or named input field
of each companion prompt.

## What Gets Generated

| Output                                             | Where      |
| -------------------------------------------------- | ---------- |
| Problem anatomy & user personas                    | Section 01 |
| Market sizing & pricing architecture               | Section 02 |
| Full feature spec with acceptance criteria         | Section 03 |
| Architecture diagram + DB schema + API contracts   | Section 04 |
| Prompt templates + RAG pipeline + cost projections | Section 05 |
| Sprint plan + team structure + risk register       | Section 06 |
| Data pipeline spec per format                      | Section 07 |
| Launch playbook + outreach copy + 90-day KPIs      | Section 08 |
