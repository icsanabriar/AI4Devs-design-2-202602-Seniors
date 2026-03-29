# Architecture decision records (ADR)

<!-- Numbered ADRs below; newest entries appended. -->

## ADR-001 — Modular monolith API with asynchronous integration worker

**Status:** Accepted  
**Date:** 2026-03-22  
**Context:**  
MVP must cover seven hiring lifecycle stages (see **001-prd.md**). **External integrations in MVP** are scoped to the **company careers page** (third-party job boards deferred per **FR-004**), **email**, **calendar** providers, and **LLM** calls behind AI features. The **assessment lifecycle** is supported via **link-out URLs** and **manual outcome capture** in-app; **assessment vendor APIs** are **deferred** (**FR-016**). **Automations** and **auditability** span stages. Team size and time-to-market favor shipping a coherent boundary before splitting services.

**Decision:**  
Deploy **one primary API application** (modular monolith) owning domain logic, RBAC, and synchronous reads/writes to the system of record. Run a separate **integration worker** process for retries, webhooks, outbound email, and provider polling—communicating via the database (outbox pattern) and/or a **message queue** *implementation detail left to implementation*.

**Options considered:**  
- **Microservices from day one** — clearer scaling seams but higher operational and integration test cost for MVP. **Rejected** for initial release.  
- **Serverless-only orchestration** — fast to prototype; cold starts, vendor coupling, and debugging complexity for long-running automations. **Deferred.**

**Consequences:**  
Clear single deployment for core logic; team must enforce **module boundaries** in code to avoid a big ball of mud. Worker scale-out remains possible without splitting the domain prematurely.

---

## ADR-002 — Multi-tenant data isolation with `organization_id`

**Status:** Accepted  
**Date:** 2026-03-22  
**Context:**  
PRD assumes multiple customer organizations; NFR-001 requires least privilege on candidate PII.

**Decision:**  
Model **every tenant-scoped row** with `organization_id` (UUID). Enforce scope in the **application layer** for MVP; evaluate **PostgreSQL Row-Level Security (RLS)** as a hardening step when compliance drivers are confirmed.

**Options considered:**  
- **Database-per-tenant** — strong isolation; operational cost and migration complexity. **Deferred** beyond regulated segments.  
- **RLS only, no app checks** — risky if any query path bypasses the ORM. **Rejected** as sole control for MVP.

**Consequences:**  
Simple backup/restore and schema evolution; requires disciplined queries and tests to prevent cross-tenant leakage.

---

## ADR-003 — PostgreSQL plus object storage for candidate documents

**Status:** Accepted  
**Date:** 2026-03-22  
**Context:**  
Applications include resumes and attachments; binaries should not bloat relational backups and should support virus scanning and retention policies later.

**Decision:**  
Store **metadata and pointers** in PostgreSQL; store **file blobs** in **S3-compatible object storage** with server-side encryption. Signed URLs for controlled download after RBAC check.

**Options considered:**  
- **Files in DB BYTEA** — simpler ops early; worse backup/restore and streaming costs. **Rejected.**  
- **External DAM** — overkill for MVP.

**Consequences:**  
Extra moving part for local dev; need lifecycle rules (retention, deletion on erasure requests—**Open question** with legal).

---

## ADR-004 — Near-real-time collaboration via WebSocket + Redis pub/sub

**Status:** Accepted  
**Date:** 2026-03-22  
**Context:**  
FR-026 requires real-time or near-real-time updates for comments and stage changes without full page refresh.

**Decision:**  
Use **WebSocket** connections terminated at the API tier (or a thin realtime gateway colocated in the same deployable for MVP), with **Redis pub/sub** (or streams) fan-out across API instances. Fall back to **polling** for clients that cannot maintain a socket. The **LTI-ICS** deliverable adopts this pattern in prose and diagrams—**UC-2** (collaboration events over **Redis** to **WebSocket** clients), **High-level system design** (**Redis** for collaboration pub/sub), and the API container view (**Collaboration** → **Redis**).

**Options considered:**  
- **SSE only** — simpler one-way push; weaker bi-directional typing indicators. **Possible alternative** if ops prefers HTTP-only.  
- **Managed realtime PaaS** — faster integration; ongoing cost and data residency questions. **Open** for later.

**Consequences:**  
Horizontal scaling of API nodes requires shared pub/sub; must authenticate socket sessions with same **Policy & RBAC** as HTTP. **WebSocket termination + Redis fan-out** is the documented baseline for FR-025/FR-026 in **LTI-ICS**; changing transport (e.g. SSE-only) requires superseding this ADR and revising the same narrative and diagrams.

---

## ADR-005 — AI assistance via orchestration module and external LLM API

**Status:** Accepted  
**Date:** 2026-03-22  
**Context:**  
FR-013, FR-031–FR-032 and NFR-011 require assistive AI, tenant toggles, traceability, and no autonomous negative decisions.

**Decision:**  
Implement an **AI orchestration** component inside the API process (module boundary) that: (1) loads **only authorized** job/application text after policy check, (2) calls an **external LLM API** over TLS, (3) persists outputs in **`ai_inference_log`** linked to the domain record, (4) never applies stage changes without a **human-initiated** command.

**Options considered:**  
- **Self-hosted model** — data residency control; higher GPU/ops burden. **Deferred** unless pilot requires it.  
- **Client-side LLM** — unacceptable leakage risk for candidate PII. **Rejected.**

**Consequences:**  
Latency and cost tied to provider; need rate limits, redaction hooks, and monitoring for prompt injection (see **Open questions** in deliverable).
