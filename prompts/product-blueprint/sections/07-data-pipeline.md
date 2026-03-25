# Section 07 — Data Pipeline Design

### Deep-Dive Companion Prompt

> **When to use this file:**
> Run this standalone when designing the data ingestion, processing, and
> storage systems. Critical for products handling multi-format documents,
> large data volumes, or real-time AI processing.

---

## Inputs

```
PRODUCT_NAME:        [Your product name]
DATA_FORMATS:        [PDF | Images | DOCX | PPT | CSV | JSON | Video | Audio | Other]
DATA_VOLUME:         [e.g. 100 docs/day at launch | 10K docs/day at scale]
LATENCY_REQUIREMENT: [Real-time (<2s) | Near-real-time (<30s) | Batch (minutes/hours)]
RETENTION_POLICY:    [How long is data stored? Any deletion requirements?]
COMPLIANCE_NEEDS:    [None | GDPR | HIPAA | SOC2]
EXISTING_STORAGE:    [None | AWS S3 | GCS | Azure Blob | Other]
```

---

## The Prompt

````
You are a data engineering architect. Design a complete, production-grade
data pipeline for the product below. Cover ingestion through retrieval.
Be specific about tools, libraries, schema, and failure handling.

INPUTS:
PRODUCT_NAME:        [FILL]
DATA_FORMATS:        [FILL]
DATA_VOLUME:         [FILL]
LATENCY_REQUIREMENT: [FILL]
RETENTION_POLICY:    [FILL]
COMPLIANCE_NEEDS:    [FILL]
EXISTING_STORAGE:    [FILL]

────────────────────────────────────────────────────────────────
OUTPUT SECTIONS
────────────────────────────────────────────────────────────────

## Ingestion Layer

For each DATA_FORMAT listed in INPUTS:

### Format: [e.g. PDF]
- **Ingestion method:** Upload endpoint | Email attachment | URL fetch |
  Webhook | API push — which and why.
- **Validation rules:**
  - Max file size and what happens if exceeded
  - MIME type check
  - Virus/malware scan (tool recommendation)
  - Content validation (is it actually a readable PDF?)
- **Ingestion API contract:**
  - Endpoint: POST /api/documents/upload
  - Request: multipart/form-data fields
  - Response: { document_id, status, estimated_processing_time }
- **Immediate storage:** Where the raw file goes before processing begins.
- **Idempotency:** How duplicate uploads are detected and handled.


## Processing Architecture

### Synchronous vs Asynchronous Decision
For each format and use case:
  - What can be done synchronously (blocking the user) — max 2–3 seconds.
  - What must be async (queued background job) — and how the user is notified.

### Job Queue Design
- **Queue technology:** (e.g. Bull/BullMQ with Redis | AWS SQS | RabbitMQ)
  with rationale.
- **Job types:** List each job type with: name, priority, retry policy, timeout.
- **Worker scaling:** How workers scale with load. Min/max worker counts.
- **Dead letter queue:** How failed jobs are handled, alerted on, and retried.
- **Job status API:** How the frontend polls or subscribes to job status.


## Extraction Pipeline

For each format, define the complete extraction process:

### Format: [e.g. PDF]
1. **Library:** (e.g. PyMuPDF, pdfplumber, AWS Textract) — why this choice.
2. **What is extracted:** Text blocks, tables, images, metadata, page numbers.
3. **Table handling:** How tables are converted to structured data.
4. **Image handling within documents:** Embedded images — extract and process
   separately with vision model? Or skip?
5. **Encoding issues:** How non-UTF8 text is handled.
6. **Scanned documents:** OCR fallback — when triggered, which tool, confidence
   threshold.
7. **Extraction quality score:** How to detect a bad extraction before indexing.

### Format: [e.g. Images]
1. **Vision model:** Claude vision | AWS Rekognition | Google Vision — which
   and when.
2. **Prompt used for image understanding:** Write the actual prompt template.
3. **Structured output format:** JSON schema of the extracted information.
4. **Handwriting / low quality:** Handling strategy and confidence thresholds.


## Chunking Strategy

### Strategy Selection
Evaluate and select the right strategy for this product:
  - **Fixed-size chunking:** Pros, cons, best for which data types.
  - **Sentence/paragraph chunking:** Pros, cons, best for which data types.
  - **Semantic chunking:** Pros, cons, best for which data types.
  - **Structural chunking** (by section/heading): Pros, cons, best for which
    data types.

**Selected strategy and justification for this product.**

### Chunk Parameters
  - Chunk size: [N tokens] — justified by Claude context window and retrieval
    performance.
  - Overlap: [N tokens] — why this amount.
  - Minimum chunk size: [N tokens] — chunks smaller than this are merged or
    discarded.
  - Maximum chunks per document: [N] — what happens when exceeded.

### Chunk Metadata Schema
```json
{
  "chunk_id": "uuid",
  "document_id": "uuid",
  "chunk_index": 0,
  "page_number": 1,
  "section_title": "string | null",
  "char_start": 0,
  "char_end": 500,
  "language": "en",
  "content_type": "text | table | image_caption",
  "created_at": "ISO8601",
  "embedding_model": "string",
  "embedding_version": "string"
}
````

## Storage Architecture

### Storage Layers

| Layer               | Technology          | What's Stored           | Access Pattern          | Retention  |
| ------------------- | ------------------- | ----------------------- | ----------------------- | ---------- |
| Raw files           | Object storage (S3) | Original uploaded files | Write once, read rarely | Per policy |
| Extracted text      | Relational DB       | Cleaned text, metadata  | Read often              | Per policy |
| Chunks + Embeddings | Vector DB           | Chunks + vectors        | High-frequency read     | Per policy |
| Job state           | Redis               | Queue jobs, status      | Ephemeral               | 7 days     |
| Processed results   | Relational DB       | AI outputs, citations   | Read often              | Per policy |

### Data Lifecycle Management

- When is data deleted? (User-initiated | Account deletion | Retention policy)
- Cascade deletion: what happens to embeddings, chunks, jobs when a document
  is deleted.
- Soft delete vs hard delete — which and why.
- GDPR right-to-erasure implementation.

## Real-Time Processing Path

For LATENCY_REQUIREMENT = Real-time:

- What can be streamed vs must be buffered.
- Claude API streaming implementation (SSE to frontend).
- WebSocket architecture for live processing updates.
- Timeout handling when Claude takes too long.

## Data Quality & Monitoring

- **Quality metrics to track:** Extraction success rate, chunk count per document,
  embedding coverage, retrieval precision@k.
- **Alerting rules:** What triggers an alert (e.g. extraction failure rate > 5%).
- **Data validation checks:** Post-processing checks before a document is marked
  "ready."
- **Observability:** What is logged at each pipeline stage. Log structure.
- **Reprocessing:** How to re-run the pipeline on a document without data
  corruption.

## Performance Benchmarks

For each format, document expected processing time at launch scale:
| Format | File Size | Extraction Time | Embedding Time | Total Pipeline Time |
|---|---|---|---|---|

Identify which step is the bottleneck and the optimization path.

```

```
