# Section 04 — Technical Architecture
### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this standalone when making foundational technology decisions, designing
> system architecture, or preparing technical documentation for engineers or
> investors.

---

## Inputs

```
PRODUCT_NAME:        [Your product name]
PRODUCT_CONTEXT:     [Paste Section 01 output OR summarize in 5–8 sentences]
DATA_FORMATS:        [PDF | Images | DOCX | Video | Audio | Structured | Other]
SCALE_TARGET:        [Expected users at launch | 6 months | 12 months]
TEAM_PROFILE:        [e.g. 1 full-stack dev | 2 backend + 1 frontend | etc.]
COMPLIANCE_NEEDS:    [None | GDPR | HIPAA | SOC2 | ISO27001]
DEPLOYMENT_TARGET:   [AWS | GCP | Azure | Self-hosted | Vercel/serverless]
EXISTING_TECH:       [Any existing code, DBs, or infrastructure to integrate with]
```

---

## The Prompt

```
You are a principal software architect with expertise in AI-native SaaS products.
Design a complete, production-grade technical architecture for the product below.
Every decision must be justified. Avoid over-engineering for the current scale
while designing for future growth.

INPUTS:
PRODUCT_NAME:        [FILL]
PRODUCT_CONTEXT:     [FILL]
DATA_FORMATS:        [FILL]
SCALE_TARGET:        [FILL]
TEAM_PROFILE:        [FILL]
COMPLIANCE_NEEDS:    [FILL]
DEPLOYMENT_TARGET:   [FILL]
EXISTING_TECH:       [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Architecture Decision Records (ADRs)

For the 5 most critical technology choices, write a mini ADR:
  - **Decision:** What was chosen.
  - **Context:** Why this choice was needed.
  - **Alternatives considered:** 2–3 other options with pros/cons.
  - **Rationale:** Why this option wins for this product's context.
  - **Consequences:** Trade-offs accepted by making this choice.


## Full Tech Stack

### Frontend
- Framework and version
- State management approach
- Key UI libraries
- File upload / streaming handling (for AI outputs)
- Real-time updates strategy (WebSocket | SSE | polling)
- Why this stack for this product

### Backend
- Language and framework
- API design (REST | GraphQL | tRPC | gRPC)
- Authentication strategy (JWT | sessions | OAuth)
- Background job processing
- Why this stack for this product

### Data Layer
- Primary database (relational): engine, schema philosophy, why
- Vector database: engine, embedding dimensions, indexing strategy, why
- Object storage: for raw files, why
- Cache layer: Redis / in-memory, what is cached, TTL strategy
- Search (if needed): full-text search approach

### AI Layer
- Claude API client setup and error handling pattern
- Model selection per feature (Haiku / Sonnet / Opus) with cost reasoning
- Streaming vs synchronous responses — when each is used
- Prompt template management (where prompts live in codebase)
- Claude API rate limiting and retry strategy

### Infrastructure
- Cloud provider and regions
- Container strategy (Docker, Kubernetes, serverless functions)
- CI/CD pipeline
- Monitoring and observability stack
- Logging strategy


## System Architecture Diagram

Draw a complete component diagram in ASCII / indented text.

Requirements:
  □ At least 8 named components
  □ Show all major data flows between components
  □ Label each connection with the protocol/method used
  □ Distinguish: User-facing | Internal services | External APIs | Storage
  □ Show where Claude API is called and from which component

Example structure to follow (adapt to this product):
```
[Browser / Mobile Client]
       │  HTTPS REST / WebSocket
       ▼
[API Gateway / Load Balancer]
       │
       ├──► [Auth Service]  ── JWT ──► [User DB]
       │
       ├──► [Document Service]
       │         │  ──► [Object Storage (S3)]
       │         │  ──► [Processing Queue]
       │                     │
       │              [Worker Service]
       │                     │  ──► [Claude API]
       │                     │  ──► [Embedding Model]
       │                     │  ──► [Vector DB]
       │
       └──► [Query Service]
                 │  ──► [Vector DB] (semantic search)
                 │  ──► [Relational DB] (metadata)
                 │  ──► [Claude API] (generation)
```


## Database Schema

### Relational DB — Core Tables
For each table: table name, purpose, columns with types and constraints,
key indexes, relationships.

### Vector DB — Collections
For each collection: collection name, vector dimensions, metadata fields,
distance metric, query patterns.

### Object Storage — Bucket Structure
Folder naming convention, access patterns, lifecycle policies.


## Multi-Format Data Processing

For each format listed in DATA_FORMATS, define the complete pipeline:

### Format: [e.g. PDF]
1. **Ingestion:** How it enters the system (upload endpoint, multipart form,
   URL fetch). Validation (size limit, type check, virus scan).
2. **Storage:** Where the raw file goes immediately.
3. **Extraction:** Library/tool used, what is extracted (text, tables, images,
   metadata).
4. **Chunking:** Strategy (fixed-size | semantic | structural), chunk size,
   overlap, metadata attached to each chunk.
5. **Embedding:** Model used, dimensions, batch size, storage target.
6. **Indexing:** How it becomes searchable — vector similarity + metadata filters.
7. **Error handling:** What happens on extraction failure, partial parse,
   corrupted file.


## API Design

List all major API endpoints:
| Method | Path | Auth | Request Body | Response | Notes |
|---|---|---|---|---|---|

Include at minimum:
  - Auth endpoints (signup, login, refresh)
  - Document management (upload, list, delete, status)
  - Query / AI interaction endpoints
  - Webhook or async job status endpoint


## Security & Privacy Architecture

- **Multi-tenancy isolation:** How one customer's data is isolated from another's.
- **Encryption:** At rest (which fields, which algorithm), in transit (TLS version).
- **Claude API key security:** Where stored, how rotated, never exposed to client.
- **PII handling:** What PII is stored, where, retention policy, deletion flow.
- **Input sanitization:** How prompt injection from user data is mitigated.
- **Compliance controls** (only those listed in COMPLIANCE_NEEDS):
  For each: what the requirement is and how the architecture satisfies it.
- **Audit logging:** What events are logged, retention period, who can access.


## Scalability Plan

- **Bottlenecks at 10x current scale:** Identify the top 3 and the solution.
- **Horizontal scaling:** Which services scale horizontally and how.
- **Claude API concurrency:** How parallel API calls are managed and throttled.
- **Database scaling path:** Read replicas, partitioning, when to shard.
- **Cost at scale:** Estimate infrastructure + Claude API cost at each scale tier
  (100 / 1,000 / 10,000 daily active users).


## Folder / File Structure

Provide a realistic, annotated project tree:

```
project-root/
├── apps/
│   ├── web/                    // Frontend application
│   │   ├── src/
│   │   │   ├── components/     // Reusable UI components
│   │   │   ├── pages/          // Route-level page components
│   │   │   ├── hooks/          // Custom React hooks
│   │   │   ├── lib/            // API client, utilities
│   │   │   └── types/          // TypeScript type definitions
│   │   └── ...
│   └── api/                    // Backend API service
│       ├── src/
│       │   ├── routes/         // API route handlers
│       │   ├── services/       // Business logic layer
│       │   ├── models/         // DB models / schemas
│       │   ├── workers/        // Background job workers
│       │   ├── claude/         // Claude API client + prompt templates
│       │   ├── pipeline/       // Document processing pipeline
│       │   └── middleware/     // Auth, validation, logging
│       └── ...
├── packages/
│   ├── shared/                 // Shared types between frontend and backend
│   └── prompts/                // Versioned prompt templates
├── infra/                      // Infrastructure as code (Terraform / CDK)
├── scripts/                    // Dev, migration, seeding scripts
└── docs/                       // Architecture docs, ADRs
```
(Expand this tree to match the actual product's structure.)
```
