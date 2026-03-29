# User Stories — LTI ATS

## Document control
- **Version:** 1.1
- **Last updated:** 2026-03-29
- **Source:** `LTI-ICS/001-prd.md` (v1.4) — 32 FRs, 11 NFRs, 14 user stories, 3 use cases, 5 phases

## Backlog overview

<!-- Sorted by priority: P0 first, then P1, P2. Within same priority: dependencies first, then business value. -->

| ID | User story | Points | Priority | Sprint | FR traceability |
|----|-----------|--------|----------|--------|-----------------|
| S-001 | As a **system admin**, I want internal users to authenticate with email and password so that only authorized personnel access the ATS. | 8 | P0 | Sprint 1 | FR-027 |
| S-002 | As a **system admin**, I want a multi-tenant database schema with organization scoping so that each customer's data is isolated. | 8 | P0 | Sprint 1 | NFR-001, ADR-002 |
| S-003 | As a **system admin**, I want role-based access control enforced at the API level so that users see only what their role permits. | 5 | P0 | Sprint 1 | NFR-001, NFR-002, FR-027 |
| S-004 | As a **system admin**, I want CI/CD pipelines and staging environments so that changes are tested and deployed reliably. | 5 | P0 | Sprint 1 | Phase 0 exit, NFR-008 |
| S-005 | As a **system admin**, I want every critical action logged with actor, timestamp, and detail so that hiring decisions are traceable. | 5 | P0 | Sprint 1 | NFR-002, FR-014 |
| S-006 | As a **recruiter**, I want to create and edit job requisitions with core fields so that I can define hiring needs accurately. | 5 | P0 | Sprint 2 | FR-001 |
| S-007 | As a **recruiter**, I want to submit requisitions for approval and receive notifications on outcome so that I can act without manual follow-up. | 5 | P0 | Sprint 2 | FR-002 |
| S-008 | As a **recruiter**, I want to publish approved jobs to the company careers page so that candidates can find and apply to open roles. | 8 | P0 | Sprint 2 | FR-004 |
| S-009 | As a **candidate**, I want to apply to a job without creating an account so that I can submit my application quickly. | 8 | P0 | Sprint 2 | FR-007, NFR-005 |
| S-012 | As a **recruiter**, I want to view applications in a pipeline Kanban board so that I can triage candidates by stage at a glance. | 8 | P0 | Sprint 3 | FR-011 |
| S-013 | As a **recruiter**, I want to move a candidate to a different pipeline stage so that the hiring team always sees current status. | 5 | P0 | Sprint 3 | FR-011, FR-014 |
| S-018 | As a **hiring manager**, I want to see the same pipeline view as the recruiter so that I have full context without asking for updates. | 5 | P0 | Sprint 4 | FR-025 |
| S-024 | As a **recruiter**, I want calendar integration with Google Calendar and Microsoft Outlook so that interview scheduling reflects real availability. | 8 | P0 | Sprint 5 | FR-018 |
| S-025 | As a **recruiter**, I want to propose interview slots and send calendar invites so that scheduling happens inside the ATS. | 5 | P0 | Sprint 5 | FR-018, FR-019 |
| S-026 | As a **recruiter**, I want to mark a candidate as hired and capture the start date so that the requisition fill status stays accurate. | 5 | P0 | Sprint 5 | FR-021 |
| S-010 | As a **recruiter**, I want to create requisitions from templates so that I can reduce setup time and maintain consistency. | 3 | P1 | Sprint 2 | FR-003 |
| S-011 | As a **recruiter**, I want to see posting status and source attribution for applicants so that I can track recruiting channel effectiveness. | 3 | P1 | Sprint 2 | FR-005 |
| S-014 | As a **recruiter**, I want the system to parse resumes and maintain a single candidate profile so that I avoid duplicate records. | 5 | P1 | Sprint 3 | FR-009 |
| S-015 | As a **candidate**, I want to create an account after applying so that I can track my application status and receive updates. | 8 | P1 | Sprint 3 | FR-008, FR-028 |
| S-016 | As a **recruiter**, I want to configure knockout questions per job so that unqualified applicants are flagged before manual review. | 5 | P1 | Sprint 3 | FR-010 |
| S-019 | As a **hiring manager**, I want to submit a structured scorecard for a candidate so that my evaluation is recorded and visible to the team. | 5 | P1 | Sprint 4 | FR-012 |
| S-020 | As a **recruiter**, I want real-time updates on comments and stage changes so that collaborators see changes without refreshing. | 8 | P1 | Sprint 4 | FR-026 |
| S-021 | As a **hiring manager**, I want AI-generated highlights of a resume compared to job requirements so that I can prepare for interviews faster. | 8 | P1 | Sprint 4 | FR-013, FR-031, FR-032 |
| S-022 | As a **recruiter**, I want in-app and email notifications for invites, stage changes, and reminders so that no action items are missed. | 5 | P1 | Sprint 4 | FR-019 |
| S-023 | As a **system admin**, I want AI-generated outputs linked to the target record so that inference decisions are traceable. | 3 | P1 | Sprint 4 | FR-032 |
| S-027 | As a **hiring manager**, I want interview feedback associated with the application record so that the team can review all evaluations in one place. | 3 | P1 | Sprint 5 | FR-020 |
| S-028 | As a **recruiter**, I want to share an assessment link with a candidate and manually record the outcome so that assessment tracking stays inside the ATS. | 5 | P1 | Sprint 5 | FR-015, FR-016 |
| S-029 | As a **system admin**, I want assessment results visible only to role-appropriate users so that sensitive data is protected. | 3 | P1 | Sprint 5 | FR-017 |
| S-030 | As a **recruiter**, I want basic offer management to track offer status and outcomes so that the hiring funnel is complete end-to-end. | 5 | P1 | Sprint 5 | FR-024 |
| S-017 | As a **recruiter**, I want to schedule or expire job postings aligned to requisition status so that outdated jobs are automatically removed. | 3 | P2 | Sprint 3 | FR-006 |
| S-031 | As a **system admin**, I want AI features gated by tenant-level toggles and role-based access so that each organization controls AI exposure. | 3 | P2 | Sprint 6 | FR-031 |
| S-032 | As a **recruiter**, I want rejection handled with templated messaging and consent respect so that candidates receive professional, compliant communication. | 5 | P2 | Sprint 6 | FR-022 |
| S-033 | As a **recruiter**, I want basic hiring funnel metrics per requisition so that I can measure pipeline efficiency. | 5 | P2 | Sprint 6 | FR-023 |
| S-034 | As a **system admin**, I want to define automation rules with triggers and actions so that repetitive tasks run without manual intervention. | 8 | P2 | Sprint 6 | FR-029 |
| S-035 | As a **system admin**, I want every automation execution logged with rule ID, actor, timestamp, and outcome so that automated actions are traceable. | 3 | P2 | Sprint 6 | FR-030 |
| S-036 | As a **system admin**, I want configurable data retention and consent flows so that the platform complies with LGPD and Ley 1581. | 8 | P2 | Sprint 6 | NFR-003, NFR-004, NFR-005 |
| S-037 | As a **system admin**, I want to export candidate data in a structured format so that the platform can fulfill regulatory data portability requests. | 5 | P2 | Sprint 6 | NFR-006 |

## Sprint plan

### Sprint 1 — Foundation and infrastructure

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (Apr 1–Apr 14) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 0 — Setup |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-001 | Internal user authentication (email + password) | 8 | P0 | FR-027 | To Do |
| S-002 | Multi-tenant database schema + organization scoping | 8 | P0 | NFR-001, ADR-002 | To Do |
| S-003 | Role-based access control at API level | 5 | P0 | NFR-001, NFR-002 | To Do |
| S-004 | CI/CD pipeline and staging environments | 5 | P0 | Phase 0 exit, NFR-008 | To Do |
| S-005 | Audit event logging framework | 5 | P0 | NFR-002, FR-014 | To Do |

**Sprint total: 31 points** (within 35 pt velocity minus 15% buffer = 30 pts effective; slightly above but all stories are foundational blockers)

#### Dependencies and risks

- S-002 (schema) blocks all data-dependent stories in Sprint 2+.
- S-001 (auth) blocks any authenticated API endpoint.
- S-003 (RBAC) blocks permission-gated features.
- **Risk:** Calendar/email provider OAuth setup may need early credential provisioning during Sprint 1 even though integration stories are later.

### Sprint 2 — Job creation, posting, and application intake

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (Apr 15–Apr 28) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 1 — Core pipeline (first half) |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-006 | Create and edit job requisitions | 5 | P0 | FR-001 | To Do |
| S-007 | Requisition approval workflow | 5 | P0 | FR-002 | To Do |
| S-008 | Publish approved job to careers page | 8 | P0 | FR-004 | To Do |
| S-009 | Public application form (no login) | 8 | P0 | FR-007, NFR-005 | To Do |
| S-010 | Job templates and duplication | 3 | P1 | FR-003 | To Do |
| S-011 | Posting status and source attribution | 3 | P1 | FR-005 | To Do |

**Sprint total: 32 points**

#### Dependencies and risks

- S-006 blocks S-007 (approval requires a requisition) and S-008 (publish requires approved req).
- S-008 blocks S-009 (apply form needs a published job to target).
- S-010 depends on S-006 (templates extend the requisition model).
- **Risk:** Careers page rendering scope (static vs dynamic) may affect S-008 effort.

### Sprint 3 — Pipeline view, candidate management, and review foundations

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (Apr 29–May 9) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 1 — Core pipeline (second half) |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-012 | Pipeline Kanban view | 8 | P0 | FR-011 | To Do |
| S-013 | Move candidate between pipeline stages | 5 | P0 | FR-011, FR-014 | To Do |
| S-014 | Resume parsing and candidate profile | 5 | P1 | FR-009 | To Do |
| S-015 | Candidate account and portal | 8 | P1 | FR-008, FR-028 | To Do |
| S-016 | Knockout qualification questions | 5 | P1 | FR-010 | To Do |
| S-017 | Schedule and expire postings | 3 | P2 | FR-006 | To Do |

**Sprint total: 34 points**

#### Dependencies and risks

- S-012 depends on S-009 (applications must exist to populate the pipeline).
- S-013 depends on S-012 (stage moves require the pipeline view context).
- S-014 depends on S-009 (resume parsing needs submitted applications).
- S-015 depends on S-009 (candidate account is post-apply).
- **Risk:** Resume parsing accuracy may require iteration; keep scope to extraction + display, not AI enrichment.

### Sprint 4 — Collaboration, AI assistance, and notifications

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (May 10–May 23) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 2 — Collaboration & integrations (first half) |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-018 | Shared pipeline visibility for HM | 5 | P0 | FR-025 | To Do |
| S-019 | Structured scorecard submission | 5 | P1 | FR-012 | To Do |
| S-020 | Real-time collaboration updates (WebSocket + Redis) | 8 | P1 | FR-026 | To Do |
| S-021 | AI-assisted resume highlights | 8 | P1 | FR-013, FR-031, FR-032 | To Do |
| S-022 | In-app and email notifications | 5 | P1 | FR-019 | To Do |
| S-023 | AI inference audit logging | 3 | P1 | FR-032 | To Do |

**Sprint total: 34 points**

#### Dependencies and risks

- S-018 depends on S-012 (pipeline view must exist for HM to share).
- S-019 depends on S-018 (HM needs pipeline access to submit scorecards).
- S-020 depends on S-003 (WebSocket auth uses RBAC tokens).
- S-021 depends on S-014 (resume must be parsed to summarize) and S-003 (AI feature gated by role).
- S-023 depends on S-021 (inference log captures AI outputs).
- **Risk:** LLM provider integration (latency, rate limits, prompt injection) may affect S-021 estimates.

### Sprint 5 — Interview scheduling, assessments, hiring, and offers

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (May 24–Jun 6) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 2 — Collaboration & integrations (second half) |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-024 | Calendar integration (Google + Outlook) | 8 | P0 | FR-018 | To Do |
| S-025 | Interview slot proposal and scheduling | 5 | P0 | FR-018, FR-019 | To Do |
| S-026 | Mark candidate as hired | 5 | P0 | FR-021 | To Do |
| S-027 | Interview feedback collection | 3 | P1 | FR-020 | To Do |
| S-028 | Assessment link-out and manual recording | 5 | P1 | FR-015, FR-016 | To Do |
| S-029 | Assessment results role visibility | 3 | P1 | FR-017 | To Do |
| S-030 | Basic offer management | 5 | P1 | FR-024 | To Do |

**Sprint total: 34 points**

#### Dependencies and risks

- S-024 blocks S-025 (scheduling needs calendar availability data).
- S-025 depends on S-022 (notifications for interview invites).
- S-026 depends on S-013 (hire is a terminal stage move).
- S-028 depends on S-013 (assessment is triggered from a pipeline stage).
- S-030 depends on S-026 (offer precedes or accompanies hire).
- **Phase pull-forward:** S-030 (FR-024, offer management) is placed in PRD Phase 3, but is pulled into Sprint 5 because offer tracking completes the end-to-end hiring funnel needed for UAT — without it, the hire action (S-026) leaves a gap between interview and hire that pilot customers would flag.
- **Risk:** OAuth token refresh for Google/Outlook may require dedicated error handling; plan for integration testing time.

### Sprint 6 — Automations, compliance hardening, and metrics

| Parameter | Value |
|-----------|-------|
| Sprint length | 2 weeks (Jun 7–Jun 20) |
| Team size | 5 developers |
| Estimated velocity | 35 story points |
| Buffer | 15% |
| Phase | Phase 3 — Automations, offer & hardening |

#### Stories

| ID | Story | Points | Priority | FR traceability | Status |
|----|-------|--------|----------|-----------------|--------|
| S-031 | AI tenant-configurable enablement | 3 | P2 | FR-031 | To Do |
| S-032 | Rejection with templated messaging | 5 | P2 | FR-022 | To Do |
| S-033 | Hiring funnel metrics | 5 | P2 | FR-023 | To Do |
| S-034 | Automation rule definitions | 8 | P2 | FR-029 | To Do |
| S-035 | Automation audit log | 3 | P2 | FR-030 | To Do |
| S-036 | Data retention and consent flows | 8 | P2 | NFR-003, NFR-004, NFR-005 | To Do |
| S-037 | Data export and portability | 5 | P2 | NFR-006 | To Do |

**Sprint total: 37 points** (S-031 moved from Sprint 5 to resolve capacity overload; low-risk feature-flag story absorbs into Sprint 6 without blocking dependencies)

#### Dependencies and risks

- S-035 depends on S-034 (audit log captures automation executions).
- S-036 depends on S-005 (retention events emit audit entries).
- S-037 depends on S-036 (export uses the same data scoping as retention).
- S-032 depends on S-013 (rejection is a stage outcome) and S-022 (notification delivery).
- **Risk:** Legal sign-off on consent language (AC-008) is an external dependency; S-036 should start early with placeholder templates.

### UAT — Pilot customer validation

| Parameter | Value |
|-----------|-------|
| Sprint length | 1 week (Jun 21–Jun 27) |
| Team size | 5 developers |
| Estimated velocity | Bug fixes only — no new stories |
| Phase | UAT |

No new stories. Focus: pilot customer walkthrough of AC-001 through AC-010, P0/P1 bug resolution, final sign-off (AC-010).

## Story details

<!-- Stories appear in priority order (same as Backlog overview). -->

### S-001 — Internal user authentication

**User story:**

As a **system admin**,

I want internal users to authenticate with email and password,

so that only authorized personnel can access the ATS.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** Foundation dependency — every authenticated feature blocks on auth. Maximum urgency and dependency impact; high technological maturity (standard email+password + JWT).

**Acceptance criteria (BDD):**

- **Given** an internal user with valid credentials, **when** they submit email and password on the login form, **then** they receive a JWT access token and are redirected to the dashboard within 2 seconds.
- **Given** an internal user with invalid credentials, **when** they submit email and password, **then** the system returns a 401 error with a generic message ("Invalid email or password") and does not reveal which field is wrong.
- **Given** a valid JWT, **when** the user makes any API request, **then** the token is validated and the request proceeds with the user's identity and organization context.
- **Given** an expired JWT, **when** the user makes an API request, **then** the system returns 401 and the client prompts re-authentication.

**Additional notes:**

- Auth module is internal to the ATS API (ADR-001) — not an external IdP.
- SSO (Google, Microsoft) is out of scope for MVP per PRD Decisions log.
- JWT should be short-lived (e.g. 15 min access + refresh token).
- WCAG 2.1 AA not required for internal login (only candidate-facing flows per NFR-009).

**Related user stories:**

- S-003: RBAC enforcement uses the identity established here
- S-002: User accounts stored in tenant-scoped schema

**FR traceability:** FR-027

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-002 — Multi-tenant database schema

**User story:**

As a **system admin**,

I want a multi-tenant database schema with organization scoping,

so that each customer's data is completely isolated.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** Foundation dependency — all tenant-scoped entities rely on this schema. Addresses core security (NFR-001) and data isolation (ADR-002) requirements.

**Acceptance criteria (BDD):**

- **Given** a new organization is provisioned, **when** the schema migration runs, **then** an `organizations` record and associated default pipeline stages exist in the database.
- **Given** a user in organization A, **when** they query any tenant-scoped endpoint, **then** only records with matching `organization_id` are returned.
- **Given** a user in organization A, **when** they attempt to access a record belonging to organization B by direct ID, **then** the API returns 404 (not 403) to avoid leaking existence.
- **Given** a database query path, **when** any ORM query for a tenant-scoped table executes, **then** it includes an `organization_id` filter (enforced by application-layer middleware or query interceptor).

**Additional notes:**

- MVP uses shared schema with `organization_id` column (ADR-002); RLS is a future hardening step.
- Pipeline stage definitions (`pipeline_stage_def`) are organization-scoped and seeded with defaults on org creation.
- Migration must be idempotent and support CI/CD rollback.

**Related user stories:**

- S-001: User accounts reference organization
- S-003: RBAC reads organization context from token
- S-005: Audit events are organization-scoped

**FR traceability:** NFR-001, ADR-002

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-003 — Role-based access control

**User story:**

As a **system admin**,

I want role-based access control enforced at the API level,

so that users see only what their role permits.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Critical dependency for every permission-gated feature; addresses NFR-001 (least privilege on candidate PII) and NFR-002 (audit trails). High business value for data protection.

**Acceptance criteria (BDD):**

- **Given** a user with role `recruiter`, **when** they access requisitions assigned to their organization, **then** full CRUD operations are permitted.
- **Given** a user with role `hiring_manager`, **when** they access applications on requisitions where they are a member, **then** read and comment operations are permitted but delete is denied.
- **Given** a user with role `candidate`, **when** they attempt to access the internal pipeline view, **then** the API returns 403.
- **Given** an unauthorized access attempt, **when** RBAC denies the request, **then** the denial is logged in the audit trail with actor, resource, and timestamp.
- **Given** an admin, **when** they open the Settings > Users & Roles page, **then** they can assign roles to users within their organization.

**Additional notes:**

- Role codes: `admin`, `recruiter`, `hiring_manager`, `candidate` (per PRD personas).
- Authorization decisions are centralized in a Policy module (per C4 component view).
- US-013 maps directly to this story.

**Related user stories:**

- S-001: Auth provides the identity for RBAC decisions
- S-002: Organization scoping is the tenant boundary for RBAC
- S-029: Assessment visibility depends on RBAC

**FR traceability:** NFR-001, NFR-002, FR-027

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-004 — CI/CD pipeline and environments

**User story:**

As a **system admin**,

I want CI/CD pipelines and staging environments,

so that code changes are tested and deployed reliably.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Infrastructure dependency — without CI/CD, no sprint deliverables can be validated in staging. High urgency for Phase 0 exit criteria.

**Acceptance criteria (BDD):**

- **Given** a pull request is opened against the main branch, **when** the CI pipeline triggers, **then** linting, unit tests, and build complete within 10 minutes.
- **Given** a merge to main, **when** the CD pipeline triggers, **then** the staging environment is updated with the new build within 15 minutes.
- **Given** a failed deployment, **when** the rollback procedure is invoked, **then** the previous working version is restored within 5 minutes.
- **Given** a staging environment, **when** the team accesses it, **then** it has a seeded database with test organizations, users, and sample data.
- **Given** a critical infrastructure failure (database or application), **when** the incident response procedure is triggered, **then** service is restored within 4 hours (RTO) and data loss does not exceed 1 hour (RPO), verified via PostgreSQL point-in-time recovery with continuous WAL archiving per NFR-008.

**Additional notes:**

- Cloud provider and container orchestration are implementation details (not PRD-specified).
- Database migrations run as part of the deployment pipeline.
- Phase 0 exit criterion: "Environments up; auth end-to-end working; DB migrations running."
- RTO/RPO targets (NFR-008) tighten to ≤ 1 h / ≤ 15 min in Next phase as pilot SLAs harden.

**Related user stories:**

- S-001: Auth is the first feature validated end-to-end on staging
- S-002: Schema migrations run in the pipeline

**FR traceability:** Phase 0 exit criteria, NFR-008

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-005 — Audit event logging framework

**User story:**

As a **system admin**,

I want every critical action logged with actor, timestamp, and detail,

so that hiring decisions and system changes are fully traceable.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Foundation dependency — audit trail is required by NFR-002 and consumed by downstream stories (stage changes, automation runs, AI inferences). Early implementation reduces technical risk.

**Acceptance criteria (BDD):**

- **Given** a user performs a critical action (stage change, approval, rejection, hire), **when** the action completes, **then** an `audit_event` row is inserted with `actor_user_id`, `action_code`, `entity_type`, `entity_id`, `organization_id`, and `created_at` (UTC).
- **Given** a system-triggered action (automation rule fires), **when** the action completes, **then** an audit event is logged with `actor_kind = system` and the `automation_rule_id`.
- **Given** an audit query, **when** an admin filters by date range and action type, **then** results are returned scoped to the admin's organization only.
- **Given** an audit event, **when** the record is written, **then** it is immutable — no UPDATE or DELETE is permitted on the `audit_event` table.

**Additional notes:**

- Immutable append-only table design; consider partitioning by `organization_id` and `created_at` for query performance.
- Distinct from `automation_run_log` (FR-030); automation runs may also emit audit events for critical side effects.

**Related user stories:**

- S-013: Stage changes emit audit events
- S-035: Automation audit log references this framework
- S-036: Retention/deletion actions emit audit events

**FR traceability:** NFR-002, FR-014

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-006 — Create and edit job requisitions

**User story:**

As a **recruiter**,

I want to create and edit job requisitions with core fields,

so that I can define hiring needs accurately for my organization.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Entry point for the entire hiring pipeline — all downstream workflows (posting, intake, review) depend on a requisition existing. Maximum business value and dependency impact.

**Acceptance criteria (BDD):**

- **Given** an authenticated recruiter, **when** they create a new requisition, **then** the form includes title, department, location model, employment type, description, optional compensation band, headcount, and hiring team selection.
- **Given** a recruiter fills all required fields, **when** they save the requisition, **then** it is persisted with status `draft` and an audit event is logged.
- **Given** an existing draft requisition, **when** the recruiter edits any field and saves, **then** the changes are persisted and the `updated_at` timestamp reflects the change.
- **Given** a recruiter in organization A, **when** they create a requisition, **then** the requisition's `organization_id` matches their organization.

**Additional notes:**

- Department, location, employment type, and compensation band stored in `description_json` (JSONB) for MVP flexibility per data model notes.
- Hiring team membership (`job_requisition_member`) is set during creation — at least one recruiter required.
- Maps to US-001 from the PRD.

**Related user stories:**

- S-007: Approval requires a draft requisition
- S-008: Publish requires an approved requisition
- S-010: Templates extend requisition creation

**FR traceability:** FR-001

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-007 — Requisition approval workflow

**User story:**

As a **recruiter**,

I want to submit requisitions for approval and receive notifications on outcome,

so that I can act on approved or returned requisitions without manual follow-up.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Blocks job publication — without approval, no job can be posted. Dependency factor is dominant; business value supports process control and auditability.

**Acceptance criteria (BDD):**

- **Given** a draft requisition, **when** the recruiter submits it for approval, **then** the status changes to `pending_approval` and an in-app notification is sent to the assigned approver.
- **Given** a pending requisition, **when** the approver approves it, **then** the status changes to `approved`, an audit event is logged, and the recruiter receives an in-app and email notification.
- **Given** a pending requisition, **when** the approver returns it with comments, **then** the status reverts to `draft`, the comments are visible on the requisition, and the recruiter is notified.
- **Given** a requisition not in `draft` status, **when** the recruiter attempts to submit for approval, **then** the system rejects the action with a clear error message.

**Additional notes:**

- Approval policy is configurable per organization (assumption: exact policy rules are org-specific).
- Maps to US-002 from the PRD.

**Related user stories:**

- S-006: Requisition must exist before approval
- S-008: Publish requires approved status
- S-022: Notifications deliver approval outcome

**FR traceability:** FR-002

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-008 — Publish job to careers page

**User story:**

As a **recruiter**,

I want to publish approved jobs to the company careers page,

so that candidates can find and apply to open roles immediately.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** First external-facing touchpoint of the ATS — candidates cannot enter the pipeline without a published job. High business value (revenue enablement), urgency (market presence), and dependency (blocks S-009).

**Acceptance criteria (BDD):**

- **Given** an approved requisition, **when** the recruiter clicks "Publish," **then** a `job_posting` record is created with status `published` and the job appears on the careers page within 60 seconds.
- **Given** a published job, **when** a candidate visits the careers page, **then** the job listing displays title, department, location, employment type, and an "Apply" button linking to the apply form.
- **Given** a published job, **when** the recruiter views the requisition detail, **then** the public URL of the careers page listing is visible.
- **Given** a cancelled requisition, **when** the recruiter unpublishes the job, **then** the careers page listing is removed within 60 seconds and the posting status updates to `unpublished`.

**Additional notes:**

- MVP scope: company careers page only (LTI-hosted). External job boards (LinkedIn, Computrabajo, Indeed) deferred to Next phase per FR-004.
- Integration worker may handle publish asynchronously via outbox pattern (ADR-001).
- Maps to US-003 from the PRD.

**Related user stories:**

- S-007: Publish requires approved requisition
- S-009: Apply form targets a published job
- S-011: Posting status tracked after publish

**FR traceability:** FR-004

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-009 — Public application form

**User story:**

As a **candidate**,

I want to apply to a job without creating an account,

so that I can submit my application quickly without friction.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** Candidates entering the pipeline is the core value event of the ATS. Without intake, no downstream review, assessment, or hire can occur. High business value, urgency, and user feedback alignment.

**Acceptance criteria (BDD):**

- **Given** a published job on the careers page, **when** a candidate clicks "Apply," **then** a form is displayed with fields for name, email, phone, resume upload (PDF/DOCX, max 10 MB), and profile fields relevant to the job.
- **Given** the apply form, **when** it loads, **then** a consent checkbox referencing the versioned privacy policy is displayed and must be checked before submission (LGPD + Ley 1581).
- **Given** a completed form with valid data, **when** the candidate submits, **then** an `application` record is created with `submitted_at` timestamp, a `candidate` record is created (or matched by email), and the resume is stored in object storage.
- **Given** a submission, **when** the system processes consent, **then** it stores `policy_version` and `consented_at` on the application record.
- **Given** a form with missing required fields, **when** the candidate attempts to submit, **then** inline validation errors are displayed without losing entered data.
- **Given** the apply form, **when** accessed on a mobile device, **then** the form is fully usable (responsive layout, WCAG 2.1 AA per NFR-009).

**Additional notes:**

- No login required (FR-007). Post-apply account creation is a separate story (S-015).
- Email is the deduplication key for candidates per PRD Decisions log.
- Maps to US-010 from the PRD.

**Related user stories:**

- S-008: Published job provides the application target
- S-014: Resume parsing processes the uploaded document
- S-015: Candidate account creation happens post-apply

**FR traceability:** FR-007, NFR-005

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-012 — Pipeline Kanban view

**User story:**

As a **recruiter**,

I want to view applications in a pipeline Kanban board,

so that I can triage candidates by stage at a glance.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** Central interface for daily recruiter work — without the pipeline view, no triage or stage management is possible. High business value, urgency, and user feedback impact. P95 response time ≤ 2 seconds (NFR-007).

**Acceptance criteria (BDD):**

- **Given** a recruiter with applications on a requisition, **when** they open the pipeline view, **then** candidates are displayed as cards in columns representing pipeline stages, grouped by stage.
- **Given** the pipeline view, **when** it loads, **then** each card shows candidate name, current stage, time-in-stage, and the pipeline owner (derived from `primary_recruiter` on `job_requisition_member`).
- **Given** 50 concurrent internal users, **when** the pipeline view loads, **then** the API response completes within 2 seconds (P95) per NFR-007.
- **Given** the pipeline view, **when** another user moves a candidate stage (and S-020 is available), **then** the view updates without full page refresh.
- **Given** a recruiter in organization A, **when** they view the pipeline, **then** only applications belonging to their organization's requisitions are shown.

**Additional notes:**

- Pipeline owner resolution per data model notes: prefer `primary_recruiter` from `job_requisition_member`; fallback to sole recruiter or "unassigned."
- Maps to US-004 from the PRD.

**Related user stories:**

- S-009: Applications populate the pipeline
- S-013: Stage moves happen from this view
- S-018: HM sees the same view with read + comment permissions

**FR traceability:** FR-011

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-013 — Move candidate between pipeline stages

**User story:**

As a **recruiter**,

I want to move a candidate to a different pipeline stage,

so that the hiring team always sees the current status.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Core pipeline operation — stage progression drives the entire hiring workflow. High business value and dependency (blocks assessment, interview, and hire stories).

**Acceptance criteria (BDD):**

- **Given** a candidate card in the pipeline view, **when** the recruiter drags it to a new stage column (or uses a dropdown), **then** the application's `current_stage_id` is updated and an `application_stage_history` record is created.
- **Given** a stage change, **when** it completes, **then** an `audit_event` is logged with the actor, previous stage, new stage, and timestamp.
- **Given** a stage change, **when** other collaborators are viewing the same pipeline, **then** the change is reflected in near-real-time (when S-020 WebSocket is available) or on next refresh.
- **Given** a stage change to a terminal stage (hired/rejected), **when** the move completes, **then** the system prompts for outcome confirmation (hire details or rejection template).

**Additional notes:**

- Stage history is immutable (append-only `application_stage_history`).
- Maps to US-005 from the PRD.

**Related user stories:**

- S-012: Pipeline view provides the stage-move UI
- S-005: Audit logging captures stage changes
- S-026: Hired is a terminal stage move
- S-032: Rejection is a terminal stage move

**FR traceability:** FR-011, FR-014

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-018 — Shared pipeline visibility for hiring manager

**User story:**

As a **hiring manager**,

I want to see the same pipeline view as the recruiter,

so that I have full context on candidate progress without asking for status updates.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Real-time collaboration between recruiter and HM is a core LTI differentiator. Urgency driven by market positioning; dependency for scorecard and feedback workflows.

**Acceptance criteria (BDD):**

- **Given** a hiring manager assigned to a requisition, **when** they open the pipeline view, **then** they see the same candidate cards and stage columns as the recruiter.
- **Given** a hiring manager, **when** they view candidate details, **then** they have read access to application data, resume, and comment threads.
- **Given** a hiring manager, **when** they attempt to delete a candidate or modify requisition settings, **then** the action is denied per RBAC.
- **Given** the pipeline view, **when** the HM and recruiter are both viewing, **then** stage changes by either user are visible to the other in near-real-time (when S-020 is available).

**Additional notes:**

- HM has read + comment access, not full CRUD. No separate login or portal — same web app with role-based views.
- Maps to US-007 from the PRD.

**Related user stories:**

- S-012: Pipeline view is the shared interface
- S-003: RBAC controls HM permission boundaries
- S-019: Scorecards require pipeline access

**FR traceability:** FR-025

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-024 — Calendar integration (Google + Outlook)

**User story:**

As a **recruiter**,

I want calendar integration with Google Calendar and Microsoft Outlook,

so that interview scheduling reflects real availability of participants.

**Story points:** 8  
**Priority:** P0  
**Priority justification:** Interview scheduling is a critical pipeline step (UC-3). Calendar integration eliminates manual coordination — high business value and user feedback impact. Technological risk requires early implementation.

**Acceptance criteria (BDD):**

- **Given** an admin in Settings > Integrations, **when** they connect Google Calendar via OAuth, **then** the system stores a valid refresh token and reads calendar availability for organization users.
- **Given** an admin in Settings > Integrations, **when** they connect Microsoft Outlook via Microsoft Graph API (OAuth), **then** the system stores a valid refresh token and reads calendar availability.
- **Given** a connected calendar, **when** the recruiter views an interviewer's availability, **then** free/busy blocks are displayed for the next 14 days with maximum 5-second load time.
- **Given** an OAuth token that has expired, **when** the system attempts to read availability, **then** it refreshes the token automatically or prompts re-authentication if the refresh fails.
- **Given** a calendar API failure, **when** the integration worker retries, **then** structured error logs are emitted per NFR-010 and the user sees a clear error message.

**Additional notes:**

- Both Google and Outlook are in-scope for MVP per PRD Decisions log.
- Integration worker handles retries and dead letters (ADR-001).
- OAuth credentials must be securely stored (encrypted at rest).

**Related user stories:**

- S-025: Scheduling uses availability data from this integration
- S-022: Interview invites trigger notifications

**FR traceability:** FR-018

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-025 — Interview slot proposal and scheduling

**User story:**

As a **recruiter**,

I want to propose interview slots and send calendar invites,

so that scheduling happens inside the ATS without switching tools.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Directly addresses recruiter pain of manual scheduling (PRD problem statement). Dependency on S-024 for availability data; high business value for recruiter efficiency.

**Acceptance criteria (BDD):**

- **Given** a candidate in an interview stage, **when** the recruiter proposes time slots, **then** the system shows available times from connected calendars of selected interviewers.
- **Given** selected time slots, **when** the recruiter confirms, **then** calendar events are created in the interviewers' calendars and an email notification is sent to the candidate.
- **Given** a scheduled interview, **when** the candidate confirms attendance, **then** the interview record status updates to `confirmed`.
- **Given** a scheduled interview, **when** any participant's calendar event is cancelled externally, **then** the system detects the change (on next sync) and updates the interview status.

**Additional notes:**

- Interview record stored in `interview` table with `participant_json` for flexible attendee tracking.
- Maps to UC-3 flow in the PRD.

**Related user stories:**

- S-024: Calendar integration provides availability data
- S-027: Interview feedback is collected post-interview
- S-022: Invites and reminders use the notification system

**FR traceability:** FR-018, FR-019

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-026 — Mark candidate as hired

**User story:**

As a **recruiter**,

I want to mark a candidate as hired and capture the start date,

so that the requisition fill status stays accurate.

**Story points:** 5  
**Priority:** P0  
**Priority justification:** Terminal pipeline event — completes the hiring funnel. Business value for requisition tracking and funnel metrics; dependency for offer management and reporting.

**Acceptance criteria (BDD):**

- **Given** a candidate at a terminal interview stage, **when** the recruiter marks them as "Hired," **then** the application's `outcome_code` is set to `hired`, `hired_at` is recorded, and the recruiter is prompted for `start_date`.
- **Given** a hire action, **when** it completes, **then** `job_requisition.filled_count` increments by 1 and an audit event is logged.
- **Given** `filled_count` reaches `headcount`, **when** the hire is recorded, **then** `job_requisition.filled_at` is set and the requisition status updates to `filled`.
- **Given** a hire, **when** the candidate has an account, **then** their portal shows the updated status.

**Additional notes:**

- Maps to FR-021 and part of UC-3 flow.
- Requisition fill logic per data model notes: `filled_at` set when `filled_count >= headcount` or manual close.

**Related user stories:**

- S-013: Hired is a terminal stage move
- S-030: Offer precedes hire in many workflows
- S-033: Funnel metrics consume hire data

**FR traceability:** FR-021

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-010 — Job templates and duplication

**User story:**

As a **recruiter**,

I want to create requisitions from templates,

so that I can reduce setup time and maintain consistency across postings.

**Story points:** 3  
**Priority:** P1  
**Priority justification:** Efficiency enhancement — reduces recruiter effort for repetitive roles. Moderate business value; no blocking dependencies; low implementation cost.

**Acceptance criteria (BDD):**

- **Given** an existing requisition or a saved template, **when** the recruiter selects "Duplicate" or "Create from template," **then** a new draft requisition is created with all fields pre-populated from the source.
- **Given** a pre-populated draft, **when** the recruiter edits any field and saves, **then** only the modified draft is updated — the source template/requisition is unchanged.
- **Given** the template library, **when** the recruiter opens it, **then** templates are listed with title, department, and last-used date, filterable by department.

**Additional notes:**

- Templates are stored as requisition records with a `is_template` flag or a separate lightweight table.
- Maps to US-001 (template library accessible) and FR-003.

**Related user stories:**

- S-006: Templates extend the base requisition model

**FR traceability:** FR-003

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-011 — Posting status and source attribution

**User story:**

As a **recruiter**,

I want to see posting status and source attribution for applicants,

so that I can track which recruiting channels are most effective.

**Story points:** 3  
**Priority:** P1  
**Priority justification:** Analytics enablement — without source attribution, channel optimization is impossible. Moderate business value; low implementation cost; depends on S-008 (posting exists).

**Acceptance criteria (BDD):**

- **Given** a published job, **when** the recruiter views the requisition detail, **then** posting status (`published`, `unpublished`, `expired`) is displayed with timestamp.
- **Given** an application submitted via the careers page, **when** it is recorded, **then** the source is attributed as `careers_page` on the application record.
- **Given** multiple applications on a requisition, **when** the recruiter views the pipeline, **then** source attribution is visible on candidate cards or in a filter/grouping option.

**Additional notes:**

- MVP supports only `careers_page` as a source. External board sources deferred to Next phase.

**Related user stories:**

- S-008: Posting creates the tracked channel
- S-033: Funnel metrics consume source data

**FR traceability:** FR-005

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-014 — Resume parsing and candidate profile

**User story:**

As a **recruiter**,

I want the system to parse resumes and maintain a single candidate profile,

so that I avoid duplicate records and have structured data for review.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Enables structured candidate data for pipeline review and AI highlights. High business value for recruiter efficiency; moderate risk on parsing accuracy. Depends on S-009 (applications with resumes).

**Acceptance criteria (BDD):**

- **Given** a submitted application with a resume (PDF or DOCX), **when** the system processes it, **then** key fields (name, email, phone, work experience, education) are extracted and stored on the candidate profile.
- **Given** a candidate who applies to a second job with the same email, **when** the application is submitted, **then** the system links it to the existing candidate profile (deduplication by email).
- **Given** a parsing failure (corrupt file, unsupported format), **when** the system cannot extract data, **then** the application is still accepted, the raw resume is accessible, and a parsing-failed flag is set.
- **Given** an admin, **when** they identify duplicate candidates (different emails, same person), **then** they can initiate a manual merge.

**Additional notes:**

- Email as primary deduplication key per PRD Decisions log.
- Resume stored in object storage (ADR-003); metadata in PostgreSQL.
- Maps to FR-009 and part of US-004.

**Related user stories:**

- S-009: Resume is uploaded during application
- S-021: AI highlights require parsed resume data

**FR traceability:** FR-009

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-015 — Candidate account and portal

**User story:**

As a **candidate**,

I want to create an account after applying,

so that I can track my application status and receive updates.

**Story points:** 8  
**Priority:** P1  
**Priority justification:** Candidate experience differentiator — reduces "black hole" perception. High user feedback value; depends on S-009 (application exists). Addresses FR-008 and FR-028.

**Acceptance criteria (BDD):**

- **Given** a successful application submission, **when** the confirmation screen loads, **then** it offers an account creation option (email + password).
- **Given** the candidate creates an account, **when** they log in to the portal, **then** they see a list of their active applications with current stage and last-updated timestamp.
- **Given** a candidate with an account, **when** their application moves to a new stage, **then** they receive an email notification referencing the job title and new stage name.
- **Given** the candidate portal, **when** accessed on a mobile device, **then** it is fully responsive and meets WCAG 2.1 AA (NFR-009).
- **Given** a candidate without an account, **when** they attempt to access the portal, **then** they are directed to create one using the email from their application.

**Additional notes:**

- Candidate auth uses email + password (FR-028); SSO deferred.
- Portal scope for MVP: application list, status, messages. No resume editing.
- Maps to US-011 and US-012.

**Related user stories:**

- S-009: Application triggers the account creation offer
- S-022: Notifications deliver stage change updates to candidates

**FR traceability:** FR-008, FR-028

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-016 — Knockout qualification questions

**User story:**

As a **recruiter**,

I want to configure knockout questions per job,

so that unqualified applicants are flagged before manual review.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Efficiency gain — reduces manual triage for high-volume roles. Moderate business value; depends on S-006 (requisition with configurable fields) and S-009 (apply form).

**Acceptance criteria (BDD):**

- **Given** a recruiter editing a requisition, **when** they add knockout questions (yes/no or minimum threshold), **then** the questions are stored and appear on the public apply form for that job.
- **Given** a candidate submitting an application, **when** their answers fail a knockout criterion, **then** the application is flagged as "below threshold" in the pipeline (not auto-rejected — human review required per FR-010).
- **Given** a flagged application, **when** the recruiter views it in the pipeline, **then** the knockout flag is visible with the specific disqualifying answers.
- **Given** a flagged application, **when** the recruiter reviews it, **then** they can override the flag and advance the candidate.

**Additional notes:**

- Human review of edge cases required per FR-010 — no autonomous rejection.
- Questions are per-requisition, stored in requisition metadata (JSONB).

**Related user stories:**

- S-006: Requisition provides the configuration surface
- S-009: Apply form renders the questions

**FR traceability:** FR-010

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-019 — Structured scorecard submission

**User story:**

As a **hiring manager**,

I want to submit a structured scorecard for a candidate,

so that my evaluation is recorded and visible to the recruiting team.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Collaboration-critical — structured feedback enables data-driven hiring decisions. High business value; depends on S-018 (HM has pipeline access).

**Acceptance criteria (BDD):**

- **Given** a hiring manager viewing a candidate profile, **when** they open the scorecard form, **then** it displays rating fields (e.g., 1–5 scale) and a free-text section.
- **Given** a completed scorecard, **when** the HM submits it, **then** a `feedback` record is created with `scorecard_json`, `author_user_id`, and `created_at`.
- **Given** a submitted scorecard, **when** the recruiter views the candidate profile, **then** the scorecard is visible in the feedback section with the HM's name and submission date.
- **Given** a scorecard submission, **when** it saves, **then** an in-app notification is sent to the recruiter on that requisition.

**Additional notes:**

- Scorecard schema stored as JSONB for flexibility (evolving rating dimensions).
- Maps to US-008.

**Related user stories:**

- S-018: HM needs pipeline access to reach the candidate profile
- S-020: Scorecard submission triggers a real-time collaboration event
- S-027: Interview feedback extends scorecards

**FR traceability:** FR-012

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-020 — Real-time collaboration updates

**User story:**

As a **recruiter**,

I want real-time updates on comments and stage changes,

so that collaborators see changes without manually refreshing the page.

**Story points:** 8  
**Priority:** P1  
**Priority justification:** Core differentiator for LTI — "opinionated collaboration" requires near-real-time feedback loops. High business value; technological risk (WebSocket + Redis) warrants early attention per ADR-004.

**Acceptance criteria (BDD):**

- **Given** two users viewing the same pipeline, **when** one moves a candidate to a new stage, **then** the other sees the update within 2 seconds without refreshing.
- **Given** a user viewing a candidate profile, **when** another user posts a comment, **then** the comment appears in the thread within 2 seconds.
- **Given** a WebSocket connection, **when** it drops, **then** the client falls back to polling (every 5 seconds) until the connection is re-established.
- **Given** the WebSocket endpoint, **when** a client connects, **then** the connection is authenticated with the same JWT used for REST API calls.

**Additional notes:**

- Implementation: WebSocket + Redis pub/sub fan-out (ADR-004).
- Polling fallback for environments that cannot maintain WebSocket connections.

**Related user stories:**

- S-012: Pipeline view is the primary consumer of real-time updates
- S-019: Scorecard submissions emit collaboration events
- S-003: WebSocket auth uses the same RBAC framework

**FR traceability:** FR-026

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-021 — AI-assisted resume highlights

**User story:**

As a **hiring manager**,

I want AI-generated highlights of a resume compared to job requirements,

so that I can prepare for interviews faster.

**Story points:** 8  
**Priority:** P1  
**Priority justification:** AI assistance is a key differentiator for LTI. High business value for hiring efficiency; moderate technological risk (LLM integration, latency, prompt injection). Depends on parsed resume (S-014) and RBAC (S-003).

**Acceptance criteria (BDD):**

- **Given** a candidate profile with a parsed resume, **when** the HM clicks "AI Highlights," **then** the system displays a summary comparing candidate qualifications to job requirements within 5 seconds.
- **Given** the AI summary, **when** it is displayed, **then** it is clearly labeled as "AI-generated" with a timestamp and rationale snippets referencing specific resume sections.
- **Given** the AI summary, **when** it is generated, **then** an `ai_inference_log` record is created linking output to the application, model name, and requesting user.
- **Given** the AI feature, **when** the tenant has disabled AI via configuration, **then** the "AI Highlights" button is hidden.
- **Given** the AI summary, **when** it suggests the candidate is a weak match, **then** no automatic stage change occurs — only the human can act on the information (NFR-011).

**Additional notes:**

- AI orchestration module calls external LLM over TLS (ADR-005).
- Prompt must use only RBAC-authorized data (redacted PII where appropriate).
- Maps to US-009.

**Related user stories:**

- S-014: Resume parsing provides structured input for AI
- S-023: Inference logging captures AI outputs
- S-031: Tenant-level AI toggles control feature availability

**FR traceability:** FR-013, FR-031, FR-032

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-022 — In-app and email notifications

**User story:**

As a **recruiter**,

I want in-app and email notifications for invites, stage changes, and reminders,

so that no action items are missed by any team member.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Notification infrastructure underpins multiple user journeys (approvals, scorecards, interviews, candidate updates). High business value for retention; dependency factor for many downstream stories.

**Acceptance criteria (BDD):**

- **Given** a stage change on an application, **when** it completes, **then** in-app and email notifications are sent to all collaborators on the requisition and to the candidate (if they have an account).
- **Given** an interview invite, **when** the recruiter schedules it, **then** email notifications are sent to all participants with calendar details.
- **Given** a user viewing the ATS, **when** a new notification arrives, **then** it appears in the notification bell within 3 seconds (when WebSocket is connected) without page refresh.
- **Given** a notification email, **when** it is sent, **then** it includes the job title, action description, and a deep link to the relevant page in the ATS.
- **Given** an email delivery failure, **when** the integration worker retries, **then** a structured error log is emitted per NFR-010.

**Additional notes:**

- Email delivery via a managed provider (SES or similar) per PRD dependencies.
- In-app notifications stored for retrieval; email is fire-and-forget with retry.
- Maps to US-002 (approval notifications), US-012 (candidate notifications), FR-019.

**Related user stories:**

- S-007: Approval notifications
- S-015: Candidate stage change notifications
- S-025: Interview invite notifications

**FR traceability:** FR-019

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-023 — AI inference audit logging

**User story:**

As a **system admin**,

I want AI-generated outputs linked to the target record,

so that inference decisions are traceable for compliance and quality review.

**Story points:** 3  
**Priority:** P1  
**Priority justification:** Regulatory and compliance necessity — AI traceability required by FR-032 and NFR-011. Low implementation cost given S-021 already calls the AI module; logging is the persistence layer.

**Acceptance criteria (BDD):**

- **Given** an AI summary is generated for an application, **when** the inference completes, **then** an `ai_inference_log` row is inserted with `application_id`, `requested_by_user_id`, `model_name`, `prompt_hash`, `output_json`, and `created_at`.
- **Given** an admin or auditor, **when** they query inference logs for an application, **then** all AI outputs for that application are returned in chronological order, scoped to the organization.
- **Given** an AI inference log, **when** it is written, **then** it is immutable (no UPDATE or DELETE permitted).

**Additional notes:**

- Retention policy for AI inference logs is TBD per PRD (labeled as open question).
- `prompt_hash` avoids storing full prompts with PII; the hash enables deduplication and reproducibility checks.

**Related user stories:**

- S-021: AI highlights generate the outputs being logged
- S-005: General audit framework provides the pattern

**FR traceability:** FR-032

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-027 — Interview feedback collection

**User story:**

As a **hiring manager**,

I want interview feedback associated with the application record,

so that the team can review all evaluations in one place.

**Story points:** 3  
**Priority:** P1  
**Priority justification:** Completes the interview workflow — without feedback collection, interview outcomes are undocumented. Moderate business value; low implementation cost (extends scorecard model).

**Acceptance criteria (BDD):**

- **Given** a completed interview, **when** the interviewer opens the application profile, **then** a feedback form is available linked to the specific interview record.
- **Given** a submitted interview feedback, **when** saved, **then** it is stored as a `feedback` record linked to both the `application` and the `interview`, visible on the candidate profile.
- **Given** multiple interviews for one application, **when** the recruiter views the profile, **then** all interview feedback entries are listed chronologically with interviewer name and date.

**Additional notes:**

- Feedback stored in `feedback_json` on the `interview` record and/or as a separate `feedback` row.
- Maps to FR-020.

**Related user stories:**

- S-025: Interview scheduling creates the interview record
- S-019: Extends the structured scorecard pattern

**FR traceability:** FR-020

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-028 — Assessment link-out and manual recording

**User story:**

As a **recruiter**,

I want to share an assessment link with a candidate and manually record the outcome,

so that assessment tracking stays inside the ATS without needing a vendor API.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Enables the assessment stage of UC-3 without vendor API dependency. Business value for pipeline completeness; technological maturity is high (signed URL generation is well-understood). Depends on S-013 (assessment is triggered from a pipeline stage).

**Acceptance criteria (BDD):**

- **Given** a candidate at the assessment stage, **when** the recruiter clicks "Send assessment link," **then** the system generates a per-application signed URL with a 72-hour expiry (`https://<domain>/assess/{application_id}?token={signed_jwt}&exp={unix_ts}`).
- **Given** the assessment link, **when** the candidate opens it in a browser, **then** they are redirected to the configured third-party assessment landing URL with the application context.
- **Given** the assessment link has expired (>72 hours), **when** the candidate opens it, **then** they see a "Link expired" message with instructions to contact the recruiter.
- **Given** the recruiter on the candidate profile, **when** they record an assessment outcome (pass/fail/pending), **then** an `assessment_attempt` record is created or updated with `status_code` and an audit event is logged.

**Additional notes:**

- Assessment vendor API integration deferred to Next phase per FR-016 and PRD Decisions log.
- Base assessment landing URL is configurable per job requisition.
- Maps to US-006 and UC-3.

**Related user stories:**

- S-013: Assessment is triggered from a pipeline stage
- S-029: Assessment results visibility is RBAC-gated

**FR traceability:** FR-015, FR-016

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-029 — Assessment results role visibility

**User story:**

As a **system admin**,

I want assessment results visible only to role-appropriate users,

so that sensitive evaluation data is protected per access control policies.

**Story points:** 3  
**Priority:** P1  
**Priority justification:** Compliance and data protection — assessment results may contain sensitive evaluations. Depends on S-028 (results must exist) and S-003 (RBAC framework).

**Acceptance criteria (BDD):**

- **Given** a recruiter, **when** they view a candidate profile with assessment results, **then** the outcome (pass/fail/pending) and score summary are displayed.
- **Given** a hiring manager, **when** they view a candidate profile, **then** assessment results are visible only if the organization's RBAC policy permits it.
- **Given** a candidate, **when** they access their portal, **then** assessment results are not displayed (internal data only).
- **Given** an unauthorized user, **when** they query the assessment API endpoint directly, **then** the API returns 403.

**Additional notes:**

- RBAC rules for assessment visibility are configurable per organization.

**Related user stories:**

- S-028: Assessment results are recorded here
- S-003: RBAC framework enforces visibility rules

**FR traceability:** FR-017

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-030 — Basic offer management

**User story:**

As a **recruiter**,

I want basic offer management to track offer status and outcomes,

so that the hiring funnel is complete from application to hire.

**Story points:** 5  
**Priority:** P1  
**Priority justification:** Completes the end-to-end hiring funnel — without offer tracking, the gap between interview and hire is undocumented. Moderate business value; depends on S-026 (hire outcome).

**Acceptance criteria (BDD):**

- **Given** a candidate at the offer stage, **when** the recruiter marks "Offer sent," **then** `application.offer_sent_at` is recorded and the candidate status updates.
- **Given** an active offer, **when** the recruiter sets an expected response date, **then** `application.offer_expected_response` is stored.
- **Given** an offer response, **when** the recruiter records the outcome (accepted/declined/no response), **then** `application.offer_outcome_code` is updated and an audit event is logged.
- **Given** an accepted offer, **when** the recruiter proceeds, **then** the flow transitions to the hire action (S-026).

**Additional notes:**

- E-signature integration is out of scope for MVP per PRD Decisions log.
- A separate `OFFER` entity may be needed post-MVP for compensation details and approval workflows.
- Maps to FR-024 and AC-005.

**Related user stories:**

- S-026: Hire follows accepted offer
- S-013: Offer is a pipeline stage

**FR traceability:** FR-024

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-017 — Schedule and expire postings

**User story:**

As a **recruiter**,

I want to schedule or expire job postings aligned to requisition status,

so that outdated jobs are automatically removed from the careers page.

**Story points:** 3  
**Priority:** P2  
**Priority justification:** Operational hygiene — prevents stale postings. Low urgency; moderate business value; low implementation cost. Depends on S-008 (posting exists).

**Acceptance criteria (BDD):**

- **Given** a recruiter publishing a job, **when** they set a future publish date, **then** the posting appears on the careers page at the scheduled time.
- **Given** a recruiter publishing a job, **when** they set an expiry date, **then** the posting is automatically removed from the careers page on that date.
- **Given** a closed or cancelled requisition, **when** the status changes, **then** associated postings are automatically unpublished.

**Additional notes:**

- Scheduled publish/expire can be handled by a background job or the integration worker.

**Related user stories:**

- S-008: Base publish functionality
- S-011: Posting status reflects schedule/expiry states

**FR traceability:** FR-006

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-031 — AI tenant-configurable enablement

**User story:**

As a **system admin**,

I want AI features gated by tenant-level toggles and role-based access,

so that each organization controls whether and how AI is used.

**Story points:** 3  
**Priority:** P2  
**Priority justification:** Governance requirement — some organizations may not want AI features enabled. Moderate business value; low implementation cost (feature flag + RBAC check).

**Acceptance criteria (BDD):**

- **Given** an admin in Settings, **when** they toggle AI features off, **then** all AI-related buttons and endpoints return a "Feature disabled" response for that organization.
- **Given** an admin, **when** they configure which roles can access AI features, **then** only those roles see AI options on candidate profiles.
- **Given** a tenant with AI disabled, **when** any user requests an AI summary via API, **then** the system returns 403 with a clear message.

**Additional notes:**

- Feature flags stored at the organization level (e.g., `organization_settings` JSONB or dedicated config table).
- Maps to FR-031.

**Related user stories:**

- S-021: AI highlights respect tenant toggles
- S-003: RBAC framework controls role-level access

**FR traceability:** FR-031

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-032 — Rejection with templated messaging

**User story:**

As a **recruiter**,

I want rejection handled with templated messaging and consent respect,

so that candidates receive professional, compliant communication.

**Story points:** 5  
**Priority:** P2  
**Priority justification:** Compliance and candidate experience — rejection templates ensure consistent, legally reviewed communication. Depends on S-013 (rejection is a terminal stage) and S-022 (email delivery).

**Acceptance criteria (BDD):**

- **Given** a recruiter rejecting a candidate, **when** they select a rejection template, **then** the template pre-fills with neutral language and includes an opt-out link for future communications.
- **Given** a rejection action, **when** it completes, **then** the candidate receives the rejection email and the application's `outcome_code` is set to `rejected`.
- **Given** a candidate who has withdrawn consent, **when** a rejection is processed, **then** the system respects the withdrawal and does not send marketing-style future communications.
- **Given** a rejection, **when** it is logged, **then** an audit event captures the actor, template used, and timestamp.

**Additional notes:**

- Final rejection copy must be reviewed by LTI Legal before production (per PRD Architectural decisions).
- Maps to FR-022, AC-008.

**Related user stories:**

- S-013: Rejection is a terminal stage move
- S-022: Email delivery for rejection messages
- S-036: Consent flows affect rejection communication

**FR traceability:** FR-022

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-033 — Hiring funnel metrics

**User story:**

As a **recruiter**,

I want basic hiring funnel metrics per requisition,

so that I can measure pipeline efficiency and identify bottlenecks.

**Story points:** 5  
**Priority:** P2  
**Priority justification:** Analytics enablement — metrics drive process improvement. Moderate business value; depends on S-013 (stage history exists) and S-026 (hire data exists).

**Acceptance criteria (BDD):**

- **Given** a requisition with applications, **when** the recruiter opens the metrics view, **then** they see time-in-stage averages, conversion rates between stages, and time-to-fill.
- **Given** the metrics view, **when** data is available, **then** metrics are calculated from `application_stage_history` timestamps and displayed per stage.
- **Given** a requisition with zero applications, **when** the metrics view loads, **then** a "No data available" message is shown.

**Additional notes:**

- PRD success metrics: time-to-fill, time-to-feedback, conversion rates.
- Initial implementation can use SQL aggregation; dashboarding can evolve later.

**Related user stories:**

- S-011: Source attribution enriches channel metrics
- S-026: Hire completion provides time-to-fill endpoint

**FR traceability:** FR-023

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-034 — Automation rule definitions

**User story:**

As a **system admin**,

I want to define automation rules with triggers and actions,

so that repetitive tasks like notifications and stage reminders run automatically.

**Story points:** 8  
**Priority:** P2  
**Priority justification:** Automation is a PRD differentiator but depends on a stable pipeline (P0 stories). Moderate urgency; high business value for recruiter efficiency; higher implementation cost (rule engine).

**Acceptance criteria (BDD):**

- **Given** an admin in Settings > Automations, **when** they create a rule, **then** they can define a trigger (e.g., "application submitted," "stale in stage for N days") and one or more actions (e.g., "notify hiring team," "create task").
- **Given** an active rule, **when** the trigger condition is met, **then** the actions execute automatically and an `automation_run_log` entry is created.
- **Given** a rule, **when** the admin toggles it off, **then** the rule stops firing but its definition and history are preserved.
- **Given** a rule execution, **when** an action fails (e.g., email delivery error), **then** the failure is logged in `automation_run_log` with error detail and the rule does not silently swallow the error.

**Additional notes:**

- Rule definitions stored as JSONB (`trigger_json`, `actions_json`) on `automation_rule`.
- Maps to US-014 and FR-029.

**Related user stories:**

- S-035: Automation audit log captures execution history
- S-022: Automation actions may trigger notifications
- S-005: Critical automation side effects emit audit events

**FR traceability:** FR-029

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-035 — Automation audit log

**User story:**

As a **system admin**,

I want every automation execution logged with rule ID, actor, timestamp, and outcome,

so that automated actions are traceable and debuggable.

**Story points:** 3  
**Priority:** P2  
**Priority justification:** Compliance and debugging necessity — automated actions must be auditable per FR-030. Depends on S-034 (automation rules must fire to produce logs).

**Acceptance criteria (BDD):**

- **Given** an automation rule fires, **when** the execution completes (success or failure), **then** an `automation_run_log` row is inserted with `automation_rule_id`, `run_at`, `actor_kind` (system/user), `status_code`, and optional `detail_json`.
- **Given** an admin, **when** they view automation history, **then** they see a chronological log of all rule executions scoped to their organization.
- **Given** a failed automation run, **when** an admin views the log, **then** the error detail is visible and the triggering conditions are described.

**Additional notes:**

- Distinct from general `audit_event` table; automation runs may also emit audit events for critical side effects per data model notes.
- Maps to US-014 and FR-030.

**Related user stories:**

- S-034: Automation rules produce the executions being logged
- S-005: General audit framework provides the baseline pattern

**FR traceability:** FR-030

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-036 — Data retention and consent flows

**User story:**

As a **system admin**,

I want configurable data retention and consent flows,

so that the platform complies with LGPD and Ley 1581 for candidate data.

**Story points:** 8  
**Priority:** P2  
**Priority justification:** Compliance critical for LATAM market launch — LGPD and Ley 1581 are non-negotiable for pilot deployment. High risk if deferred; depends on S-005 (audit events for retention actions) and S-009 (consent collected on apply).

**Acceptance criteria (BDD):**

- **Given** an admin in Settings, **when** they configure retention windows by category (active, rejected, hired, withdrawn), **then** the system enforces processing limits after the retention period expires.
- **Given** a retention period expiry, **when** the system processes scheduled archival or deletion, **then** candidate PII is purged from primary stores and search/index replicas, and an audit event is emitted with actor (system), scope, action, and timestamp.
- **Given** a candidate, **when** they withdraw consent, **then** the system updates processing flags, stops consent-dependent processing, and triggers applicable retention or erasure flows.
- **Given** a privacy/admin role, **when** they initiate manual deletion, **then** the candidate profile is anonymized or deleted and the action is logged in the audit trail.
- **Given** the apply form, **when** consent is collected, **then** it records `policy_version`, `consented_at`, and a reference to the privacy notice URL presented.

**Additional notes:**

- LGPD Art. 8, Ley 1581 Art. 9 compliance.
- Legal sign-off on retention durations is an external dependency (AC-008 gate).
- Maps to NFR-003, NFR-004, NFR-005 and AC-008, AC-009.

**Related user stories:**

- S-009: Consent collected during application
- S-005: Retention and deletion emit audit events
- S-037: Data export uses the same scoping

**FR traceability:** NFR-003, NFR-004, NFR-005

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

### S-037 — Data export and portability

**User story:**

As a **system admin**,

I want to export candidate data in a structured format,

so that the platform can fulfill regulatory data portability requests.

**Story points:** 5  
**Priority:** P2  
**Priority justification:** Compliance requirement for LGPD/Ley 1581 data portability rights. Depends on S-036 (retention scoping) and S-003 (RBAC-gated export).

**Acceptance criteria (BDD):**

- **Given** a verified data portability request, **when** an authorized admin initiates export for a candidate, **then** the system generates a JSON or CSV file containing all data pertinent to that candidate within the organization.
- **Given** an export action, **when** it completes, **then** an audit event is logged with the admin's identity, the scope of data exported, and the timestamp.
- **Given** an unauthorized user, **when** they attempt to initiate an export, **then** the system denies the request per RBAC.
- **Given** the export file, **when** downloaded, **then** it includes application data, feedback (anonymized author names if required), stage history, and consent records — but not internal scoring algorithms or AI model weights.

**Additional notes:**

- Export fulfillment is RBAC-gated per NFR-001.
- Maps to NFR-006.

**Related user stories:**

- S-036: Retention and consent flows scope the exportable data
- S-003: RBAC controls who can trigger exports

**FR traceability:** NFR-006

**INVEST validation:**
- [x] Independent
- [x] Negotiable
- [x] Valuable
- [x] Estimable
- [x] Small
- [x] Testable

---

## Assumptions and open questions

### Capacity assumptions

- **Team size:** 5 developers (3 backend, 2 frontend). No dedicated QA — testing shared with engineers.
- **Sprint length:** 2 weeks.
- **Estimated velocity:** 35 story points per sprint (conservative for a new team at ~70% focus factor).
- **Buffer:** 15% reserved per sprint for unknowns and technical debt.
- **Tech stack familiarity:** Assumed moderate — team is greenfield but experienced with web frameworks, PostgreSQL, and REST APIs. LLM integration and OAuth calendar APIs may require learning time.

### Open questions

- **AI inference log retention:** How long should `ai_inference_log` records be retained? PRD marks as TBD.
- **Resume parsing depth:** Should MVP attempt structured extraction (skills, years of experience) or limit to raw text + metadata? Affects S-014 estimate.
- **Automation rule complexity:** How many trigger types and action types are needed for MVP? Affects S-034 estimate. PRD examples suggest 2-3 trigger types (application submitted, stale stage, stage change) and 2-3 actions (notify, create task, change stage).
- **Legal sign-off timeline:** Consent language and rejection templates require LTI Legal review before AC-008 can be met. External dependency on Sprint 6 stories.

## Definition of Done

- [ ] Code is reviewed and merged to main branch.
- [ ] Unit tests cover core logic (>80% coverage on new code).
- [ ] Integration tests pass for API endpoints and external integrations.
- [ ] All acceptance criteria (BDD) pass on staging environment.
- [ ] Audit events are emitted for critical actions.
- [ ] RBAC is enforced — verified with cross-role test cases.
- [ ] No P0 or P1 bugs open against the story.
- [ ] Documentation updated (API docs, data model notes) where applicable.
- [ ] Accessibility verified for candidate-facing flows (WCAG 2.1 AA per NFR-009).
