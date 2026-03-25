# Section 05 — AI Implementation Details

### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this standalone when engineering the Claude API integration — prompt design,
> RAG pipeline, agent architecture, and cost optimization. Most technical of all
> companion files. Ideal before any AI code is written.

---

## Inputs

```
PRODUCT_NAME:        [Your product name]
PRODUCT_CONTEXT:     [Paste Section 01 output OR summarize in 5–8 sentences]
FEATURES_LIST:       [Paste Section 03 MVP features OR list them here]
DATA_FORMATS:        [PDF | Images | DOCX | Text | Structured | Other]
AGENTIC_NEEDED:      [Yes — describe the workflow | No]
DOMAIN_SENSITIVITY:  [General | Medical | Legal | Financial | Other sensitive domain]
COST_SENSITIVITY:    [Low — quality first | Medium — balance | High — minimize cost]
```

---

## The Prompt

```
You are a Claude API specialist and RAG systems architect. Design a complete
AI implementation strategy for the product below. Every recommendation must
include the specific API parameters, prompt patterns, and engineering details
needed to implement it.

INPUTS:
PRODUCT_NAME:        [FILL]
PRODUCT_CONTEXT:     [FILL]
FEATURES_LIST:       [FILL]
DATA_FORMATS:        [FILL]
AGENTIC_NEEDED:      [FILL]
DOMAIN_SENSITIVITY:  [FILL]
COST_SENSITIVITY:    [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Model Selection Matrix

For each product feature, specify:
| Feature | Model | Reason | Avg Input Tokens | Avg Output Tokens | Cost/1K calls |
|---|---|---|---|---|---|

Models to choose from:
  - claude-haiku-4-5 — fast, cheap, simple tasks
  - claude-sonnet-4-5 — balanced, complex reasoning
  - claude-opus-4-5  — highest capability, expensive

End with a routing rule:
  "Use Haiku when ___. Use Sonnet when ___. Use Opus when ___."


## Prompt Engineering Patterns

For each major feature, write the full prompt template:

### Feature: [Feature Name]
**Pattern:** [Classification | Extraction | Generation | Summarization |
             Reasoning | Agent | Other]

**System Prompt:**
```

[Write the full system prompt — include persona, constraints, output format,
and domain-specific instructions]

```

**User Message Template:**
```

[Write the template with {placeholder} variables for dynamic content]

```

**Key Design Decisions:**
  - Why this structure (why system prompt contains X)
  - Output format enforced and why (JSON | Markdown | plain text)
  - Temperature setting and reasoning
  - max_tokens setting and why

**Edge Cases Handled by Prompt:**
  - What if input is empty / too short
  - What if input is in another language
  - What if input contains sensitive content
  - What if the task is ambiguous


## Context Window Management

- **Context budget per feature:** Input tokens allocated to: system prompt |
  retrieved chunks | conversation history | user query | reserved for output.
- **Conversation history strategy:** How many turns to retain. When to summarize
  older turns. How summaries are generated and injected.
- **Document injection strategy:** How retrieved chunks are formatted and
  ordered before injection. Separator tokens / formatting between chunks.
- **Context overflow handling:** What happens when the context limit is approached.
  Truncation strategy. User notification.


## RAG Pipeline — Full Specification

### Indexing Pipeline (offline / async)

1. **Document intake:** Format detection, validation, metadata extraction.
2. **Text extraction:** Tool/library per format, fallback for failures.
3. **Pre-processing:** Cleaning (strip headers/footers, fix encoding, remove
   boilerplate). Language detection.
4. **Chunking strategy:**
   - Method: Fixed-size | Semantic | Structural (by section/paragraph)
   - Chunk size: [tokens] with [tokens] overlap — justify this choice.
   - Metadata per chunk: document_id, chunk_index, page_number, section_title,
     source_url, created_at, language.
5. **Embedding:** Model, dimensions, batch size, normalization.
6. **Storage:** Vector DB collection, index type, distance metric.
7. **Quality check:** How embedding quality is validated post-indexing.

### Retrieval Pipeline (real-time, per query)

1. **Query processing:** Query cleaning, language detection, query expansion
   (if applicable).
2. **Query embedding:** Same model as indexing. Caching strategy for repeated
   queries.
3. **Hybrid search (if applicable):** Vector similarity + keyword/BM25 fusion.
   How scores are combined.
4. **Re-ranking:** Cross-encoder re-ranking approach (if used). When it's worth
   the latency.
5. **Context assembly:** How retrieved chunks are formatted and ordered for
   injection into the Claude prompt.
6. **Citation tracking:** How source metadata flows from chunks → Claude prompt
   → response → UI display.


## Agentic Architecture (if AGENTIC_NEEDED = Yes)

### Agent Design
- **Agent objective:** What the agent is trying to accomplish.
- **Planning approach:** How the agent decides what steps to take.
- **Tool definitions:** For each tool:
```

Tool name: [name]
Description: [what it does — Claude reads this to decide when to use it]
Input schema: [field names, types, descriptions]
Output schema: [what the tool returns]
Error handling: [what to return on failure]

```
- **Human-in-the-loop points:** Where the agent must pause and ask for
confirmation before proceeding.
- **Loop termination:** How infinite loops are prevented. Max iterations.
Timeout strategy.
- **State management:** How agent state persists between steps.


## Domain-Specific AI Considerations

(Only if DOMAIN_SENSITIVITY is not "General")

For [specified domain]:
- Specific terminology the system prompt must include for accurate outputs
- Content the model should never generate or recommend (safety guardrails)
- Disclaimer requirements in outputs
- Validation steps for AI outputs before showing to users
- Regulatory implications of AI-generated content in this domain


## Cost Optimization Strategy

### Token Budget Design
For each feature, show the token budget breakdown:
[Feature] → System: X tokens | Context: Y tokens | Output: Z tokens | Total: N

### Caching Strategy
- **Prompt caching:** Which parts of the system prompt are stable enough
  for Anthropic's prompt caching feature. Expected cache hit rate.
- **Semantic caching:** For repeated or near-identical queries, how responses
  are cached and retrieved. Similarity threshold for cache hit.
- **Response caching:** Which responses can be cached and for how long.

### Model Routing Logic
Write the exact routing logic as pseudocode:
```

if query_type == "simple_lookup" and context_length < 1000:
use claude-haiku-4-5
elif requires_complex_reasoning or context_length > 10000:
use claude-opus-4-5
else:
use claude-sonnet-4-5

```

### Cost Projections
| Scale | Daily Active Users | Avg API calls/user/day | Avg tokens/call | Daily cost | Monthly cost |
|---|---|---|---|---|---|
| Launch     | 100  | ... | ... | ... | ... |
| Growth     | 1,000 | ... | ... | ... | ... |
| Scale      | 10,000 | ... | ... | ... | ... |

Include: assumptions used, what drives cost growth, and at what scale
optimization becomes critical.


## Evaluation & Quality Assurance

- **Output evaluation criteria:** For each feature, how do you measure if the
  Claude output is good? (Criteria: accuracy, relevance, format compliance,
  safety, latency.)
- **Automated evals:** What test cases to run before deploying prompt changes.
  Format of eval dataset.
- **Human review pipeline:** What outputs should humans review before showing
  to users? Who does this? At what volume does it become unsustainable?
- **Regression testing:** How to catch when a Claude model update changes
  output quality.
- **Feedback loop:** How user feedback (thumbs up/down, edits, deletions) feeds
  back into prompt improvement.
```
