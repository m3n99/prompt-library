# Section 02 — Market & Business Strategy
### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this prompt standalone when you need a rigorous go-to-market strategy,
> pricing architecture, or expansion plan. Assumes Section 01 output is available
> as context — paste it in under PRODUCT_CONTEXT.

---

## Inputs

```
PRODUCT_NAME:        [Your product name]
PRODUCT_CONTEXT:     [Paste Section 01 output OR summarize product in 5–8 sentences]
INITIAL_MARKET:      [Geographic focus — country/region]
BUDGET_RANGE:        [Bootstrap | Seed | Series A | Enterprise]
REVENUE_TARGET_Y1:   [e.g. $50K ARR | $500K ARR | $5M ARR]
TEAM_SIZE:           [Solo | 2–5 | 6–20 | 20+]
```

---

## The Prompt

```
You are a go-to-market strategist and revenue architect. Produce a detailed
market and business strategy for the product described. Every recommendation
must be tied to the product's specific context, budget, and team size.

INPUTS:
PRODUCT_NAME:        [FILL]
PRODUCT_CONTEXT:     [FILL]
INITIAL_MARKET:      [FILL]
BUDGET_RANGE:        [FILL]
REVENUE_TARGET_Y1:   [FILL]
TEAM_SIZE:           [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Market Sizing

- **TAM (Total Addressable Market):** Number of potential buyers globally.
  How calculated. Dollar value.
- **SAM (Serviceable Addressable Market):** Subset you can realistically reach
  given product, language, and go-to-market constraints. How calculated.
- **SOM (Serviceable Obtainable Market):** Realistic Year 1–2 capture.
  Methodology and assumptions labeled clearly.
- **Growth Rate:** Is this market expanding, flat, or contracting? Key drivers.


## Beachhead Segment Selection

Evaluate 5 candidate customer segments and select the best beachhead.

For each segment:
  - Segment name and description
  - Market size within SAM
  - Pain severity (1–10) for this product's core problem
  - Willingness to pay (1–10)
  - Sales cycle length
  - Ease of access (do you have a path to them?)
  - Verdict: ✅ Beachhead | ⚠️ Phase 2 | ❌ Too early

Explain the final beachhead choice in 3–4 sentences.


## Expansion Roadmap

### Phase 1 — Beachhead (Month 0–6)
- Exact segment being targeted
- Value proposition specific to this segment
- Sales motion (self-serve | inside sales | partnerships)
- Success metric that unlocks Phase 2
- Risks and contingency

### Phase 2 — Adjacent Expansion (Month 6–18)
- New segment and why they are the right next move
- What product changes or additions are needed
- How Phase 1 relationships create Phase 2 leverage

### Phase 3 — Platform / Ecosystem (Month 18+)
- How the product evolves into a platform or network
- Partner and integration ecosystem play
- Enterprise motion and what it requires


## Pricing Architecture

Design a full pricing model:

### SaaS Tier Breakdown
| Tier | Price / month | Target Persona | Key Features | Usage Limits | Upgrade Trigger |
|---|---|---|---|---|---|

### Pricing Rationale
- Why these price points (anchoring, competitor benchmarking, value-based reasoning)?
- What is the "aha moment" that justifies the upgrade from each tier?

### Alternative / Complementary Models
Evaluate each relevant model for this product:
  - Usage-based (per API call, per document, per seat)
  - Annual upfront discount strategy
  - Enterprise custom pricing — what triggers it, what it includes
  - Marketplace or reseller potential
  - Professional services / onboarding fees


## Competitive Positioning

### Competitor Matrix
| Competitor | Core Offering | Pricing | AI Capabilities | Biggest Weakness | Our Edge |
|---|---|---|---|---|---|

### Positioning Statement
Write 3 alternative positioning statements (different angles).
Recommend one and explain why.

### Battle Cards
For the top 2 competitors write a battle card:
  - Their pitch
  - Their strengths (be honest)
  - Their weaknesses
  - How to win against them (specific objection responses)


## Revenue Model & Projections

Build a simple unit economics model:
- **ACV (Annual Contract Value)** per tier
- **CAC (Customer Acquisition Cost)** estimate per channel
- **LTV (Lifetime Value)** estimate and LTV:CAC ratio
- **Payback period** per tier
- **Monthly Recurring Revenue path** to hit REVENUE_TARGET_Y1
  (How many customers per tier needed? Is it achievable given team and budget?)


## Partnerships Strategy

List 5 strategic partnership types relevant to this product:
  - Partner type (integration | distribution | referral | white-label | co-sell)
  - Example companies in each category
  - What value you bring them
  - What they bring you
  - How to approach them (cold | warm | inbound)
```
