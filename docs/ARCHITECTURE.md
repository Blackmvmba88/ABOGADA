# Architecture — ABOGADA / BlackMamba LEX

## 1. Product boundary

ABOGADA is a **legal intelligence operating system**, not an autonomous lawyer.

The system may:
- ingest and organize information;
- retrieve authorized sources;
- extract structured facts;
- generate drafts;
- detect inconsistencies;
- calculate workflow deadlines from configured legal rules;
- prepare actions for approval;
- execute explicitly authorized administrative actions.

The system must not silently convert a model inference into a legal fact, filing, payment, representation, waiver, acceptance, settlement, or external communication.

## 2. Core architecture

```text
Interfaces
  Web / Desktop / Mobile / Voice / API
                │
                ▼
        Legal Orchestrator
                │
     ┌──────────┼───────────┐
     ▼          ▼           ▼
 Policy      Agent Bus    Workflow
 Engine                   Engine
     │          │           │
     └──────────┼───────────┘
                ▼
        Domain Services
                │
 ┌──────────────┼───────────────────────┐
 ▼              ▼                       ▼
Matter       Document               Knowledge
Service      Intelligence           Graph
 │              │                       │
 ▼              ▼                       ▼
Timeline     OCR/Parsing              Relations
Evidence     Extraction               Search
Tasks        Citations                 Reasoning
                │
                ▼
        Retrieval Layer
                │
     ┌──────────┼──────────────┐
     ▼          ▼              ▼
 Relational   Vector          Object
 Database     Index           Storage
                │
                ▼
           Audit Ledger
```

## 3. Domain modules

### Matter
Owns the legal matter lifecycle.

Responsibilities:
- matter identity;
- parties and roles;
- status;
- jurisdiction metadata;
- assigned professionals;
- next action;
- permissions;
- matter-level policy.

### Client
Responsibilities:
- intake;
- identity data;
- contact channels;
- consent;
- conflict-check references;
- portal access.

### Document
Responsibilities:
- binary/source storage;
- normalized text;
- metadata;
- versions;
- page mapping;
- classification;
- extraction;
- signatures;
- references.

### Fact
A fact is never merely free text.

Suggested shape:

```json
{
  "id": "fact_x",
  "matter_id": "matter_x",
  "statement": "The delivery date was changed to 12 June.",
  "status": "asserted|corroborated|disputed|unknown",
  "source_refs": ["citation_x"],
  "event_time": null,
  "confidence": 0.0,
  "created_by": "human|model|import"
}
```

### Citation
Every model-derived legal assertion should support provenance.

```json
{
  "document_id": "doc_x",
  "page": 12,
  "location": "paragraph 3",
  "quote_hash": "sha256:...",
  "source_type": "case_file|law|precedent|email|note",
  "retrieved_at": "ISO-8601"
}
```

### Event / Timeline
Represents occurrences independently of when a document was authored.

Fields:
- event date/time;
- precision;
- source date;
- participants;
- location;
- related facts;
- supporting evidence;
- disputed flag.

### Evidence
Responsibilities:
- evidence item identity;
- source;
- custodians;
- hashes;
- chain-of-custody events;
- legal relevance tags;
- associated facts;
- derivative assets;
- access history.

### Obligation / Deadline
Separate legal obligation from operational task.

```text
OBLIGATION -> may produce -> DEADLINE -> may produce -> TASK
```

Deadline calculations must keep:
- source rule;
- jurisdiction;
- triggering event;
- calculation method;
- holidays/calendar version;
- human validation state.

### Argument
Graph node connecting:
- proposition;
- facts;
- evidence;
- authorities;
- counterarguments;
- weaknesses.

## 4. Legal Knowledge Graph

Minimum node types:
- Person
- Organization
- Matter
- Document
- Fact
- Event
- Evidence
- Obligation
- Deadline
- Argument
- Authority
- Communication
- Task

Minimum edge types:
- PARTY_TO
- REPRESENTS
- AUTHORED
- SIGNED
- SUPPORTS
- CONTRADICTS
- MENTIONS
- OCCURRED_AT
- TRIGGERS
- DUE_ON
- CITES
- RESPONDS_TO
- RELATES_TO
- DERIVED_FROM

The graph does not replace the source material. It is a navigable index over provenance.

## 5. AI agent contracts

Every agent receives:
- user identity;
- matter scope;
- permission scope;
- task;
- allowed tools;
- allowed sources;
- output schema;
- risk level.

Every agent returns:
- structured result;
- citations;
- assumptions;
- unresolved questions;
- confidence;
- proposed actions;
- audit metadata.

### Initial agents

**Document Agent**
- classify;
- OCR;
- extract;
- summarize;
- compare.

**Timeline Agent**
- identify events;
- normalize dates;
- detect inconsistencies.

**Research Agent**
- search configured legal sources;
- separate authority from commentary.

**Citation Verifier**
- confirm that a cited source exists;
- verify quoted proposition against source.

**Contract Agent**
- clause extraction;
- obligations;
- risks;
- version comparison.

**Evidence Agent**
- evidence indexing;
- metadata;
- fact linkage;
- contradictions.

**Draft Agent**
- create first drafts using approved templates and matter facts.

**Calendar Agent**
- identify potential deadlines;
- calculate with configured rules;
- require validation for legal deadlines.

**Audit Agent**
- inspect provenance and policy compliance before sensitive actions.

## 6. Model strategy

Do not couple the product to one model vendor.

Use a provider adapter:

```text
ModelGateway
  ├─ completion()
  ├─ structured()
  ├─ embeddings()
  ├─ vision()
  ├─ speech_to_text()
  └─ rerank()
```

Each run stores:
- provider;
- model;
- prompt/template version;
- retrieval set;
- output;
- approval state.

## 7. Retrieval strategy

### Matter RAG
Scope strictly to the active matter unless the user has cross-matter permission.

### Legal Research RAG
Separate index for:
- legislation;
- regulations;
- case law;
- official publications;
- selected doctrine.

Never blend internal case facts and general legal authorities without preserving source type.

## 8. Search

Search modes:
1. exact;
2. metadata;
3. full text;
4. semantic;
5. graph traversal;
6. hybrid reranked search.

Example query:

```text
“Where did the delivery date change?”
```

Expected resolution:
```text
query
 -> semantic candidate documents
 -> exact passages
 -> timeline events
 -> related contract versions
 -> cited answer
```

## 9. Workflow engine

Use event-driven workflow definitions.

Example:

```yaml
event: document.received
when:
  classification: court_notification
steps:
  - identify_matter
  - extract_dates
  - extract_orders
  - propose_deadlines
  - update_timeline
  - create_review_task
  - notify_assignee
approval:
  required_before:
    - confirm_legal_deadline
    - external_send
    - filing
```

## 10. Suggested technical stack

The implementation may evolve, but an initial practical stack:

- frontend: TypeScript + React/Next.js;
- API: TypeScript or Python/FastAPI;
- relational DB: PostgreSQL;
- vector search: pgvector first;
- object storage: S3-compatible;
- graph: PostgreSQL relations first, dedicated graph DB only when justified;
- task queue: Redis/worker or durable workflow engine;
- document parsing: pluggable parser/OCR pipeline;
- auth: RBAC + matter-level authorization;
- audit: append-only audit events.

Avoid premature infrastructure complexity.

## 11. MVP boundary

The first useful vertical slice should do exactly this:

```text
CREATE MATTER
   ↓
UPLOAD DOCUMENTS
   ↓
PARSE / OCR
   ↓
CLASSIFY
   ↓
EXTRACT PEOPLE + DATES + FACTS
   ↓
BUILD TIMELINE
   ↓
ASK QUESTION
   ↓
ANSWER WITH DOCUMENT/PAGE CITATIONS
   ↓
CREATE HUMAN-APPROVED TASK
```

If this loop is reliable, the rest of the operating system has a solid foundation.
