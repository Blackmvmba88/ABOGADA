# Roadmap — ABOGADA / BlackMamba LEX

## Phase 0 — Foundation

Goal: make one legal matter computable end-to-end.

Deliverables:
- domain model;
- matter creation;
- document upload;
- metadata;
- OCR/parser interface;
- timeline;
- citation model;
- audit events;
- role and matter permissions;
- first search endpoint.

Exit gate:
- one matter can be created;
- multiple documents can be attached;
- the system can answer a question using only those documents;
- every answer points back to document/page/location;
- every AI operation is auditable.

## Phase 1 — Matter Intelligence

Deliverables:
- automatic document classification;
- entity extraction;
- fact extraction;
- date/event extraction;
- missing-document detection;
- duplicate detection;
- semantic + exact search;
- matter dashboard;
- next-action panel.

Exit gate:
- a lawyer can open a matter and understand what happened, what is missing and what requires attention without manually opening every document.

## Phase 2 — Timeline & Contradictions

Deliverables:
- event graph;
- date normalization;
- document-date vs event-date separation;
- contradiction detector;
- timeline UI;
- evidence-to-fact links;
- unresolved-question queue.

Exit gate:
- the system can explain why two statements appear inconsistent and cite both sources without deciding the disputed fact itself.

## Phase 3 — Legal Research

Deliverables:
- jurisdiction adapters;
- official-source registry;
- legislation ingestion;
- case-law ingestion;
- source validity metadata;
- citation verifier;
- research notebook;
- legal-change monitor.

Exit gate:
- research answers distinguish case facts, legal authorities and commentary;
- authorities are verifiable;
- unavailable sources are never invented.

## Phase 4 — Draft & Review

Deliverables:
- approved template library;
- variable-driven document generation;
- clause library;
- contract review;
- redline/comparison;
- filing-document validator;
- annex detector and index generator.

Exit gate:
- drafts can be generated entirely from approved matter data and templates;
- every inserted factual assertion can be traced to its source.

## Phase 5 — Evidence & Strategy

Deliverables:
- evidence catalog;
- hashing;
- chain-of-custody log;
- media transcription;
- theory-of-case workspace;
- argument graph;
- adversarial review;
- deposition/interrogation preparation.

Exit gate:
- each argument can be navigated to supporting facts, evidence and authorities.

## Phase 6 — Workflow OS

Deliverables:
- workflow engine;
- deadlines;
- tasks;
- calendar;
- email integration;
- communication routing;
- client portal;
- approvals;
- notifications.

Exit gate:
- a received legal document can trigger a controlled workflow from intake to human-approved next action.

## Phase 7 — Law Firm Operations

Deliverables:
- CRM;
- conflict checks;
- time tracking;
- expenses;
- billing;
- accounts receivable;
- matter profitability;
- team workload;
- management dashboard.

## Phase 8 — Agent Mesh

Deliverables:
- Legal Orchestrator;
- Document Agent;
- Timeline Agent;
- Research Agent;
- Citation Verifier;
- Contract Agent;
- Evidence Agent;
- Draft Agent;
- Calendar Agent;
- Audit Agent.

Agent rule:
- agents propose;
- policy decides what they are allowed to attempt;
- humans approve sensitive actions;
- audit records everything.

## First vertical slice

The first implementation should stay deliberately small:

1. Create matter.
2. Upload PDF/image/text document.
3. Parse/OCR.
4. Extract people, dates, facts and document type.
5. Build timeline.
6. Ask natural-language questions.
7. Return cited answer.
8. Create a follow-up task.
9. Record audit trail.

That slice proves the core product before adding dozens of integrations.

## Priority labels

- **P0** — provenance, permissions, matter model, documents, timeline, citations, audit.
- **P1** — contradiction detection, search, draft/review, legal research.
- **P2** — workflow, calendar, client portal, communications.
- **P3** — billing, CRM, advanced simulations, analytics.

## Definition of done

A feature is not done merely because an LLM can produce an answer.

For legal-grade completion it should satisfy, when applicable:
- source traceability;
- deterministic schema validation;
- permission checks;
- audit event;
- error state;
- human review boundary;
- test coverage;
- versioned prompt/rule;
- jurisdiction metadata.
