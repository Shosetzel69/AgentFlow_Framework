# AgentFlow Governance

Status: `REFERENCE CORE`  
Document version: `1.2.0`  
Framework compatibility: `1.2.x`

## 1. Decision model

The project has one or more authorized human approvers. AI agents may analyze, recommend, execute approved work, and provide evidence, but they do not silently assume authority over material scope, architecture, security, privacy, cost, or production release decisions.

There is no automatic transition from discussion to implementation.

## 2. Normative process definition

This section is the **single normative end-to-end process definition** for AgentFlow. Other documents may explain individual phases or adoption procedures, but they do not redefine the process sequence.

| Step | Phase / outcome | Required authority or condition |
|---|---|---|
| 1 | REQUIREMENTS | Requirement is analyzed and made ready for approval |
| 2 | REQUIREMENT_APPROVED | `APPROVE_REQUIREMENT <ref>` is durably recorded |
| 3 | ARCHITECTURE, when triggered | Material architecture questions are decided before executable planning continues |
| 4 | DEVELOPMENT_ANALYSIS | Approved intent is converted into implementable slices and proposed ATCs |
| 5 | TASK_CONTRACT | Exact ATC is proposed and approved |
| 6 | IMPLEMENTATION | `APPROVE_TASK_CONTRACT <ref>` is durably recorded for the exact ATC |
| 7 | EVIDENCE | Executor produces an Evidence Bundle for the exact implementation candidate |
| 8 | REVIEW | Independent Review returns a verdict bound to that exact candidate identity |
| 9 | DEV / CANDIDATE | DEV verification passes and a complete Candidate Manifest is recorded for the exact reviewed candidate |
| 10 | TEST | TEST validates the exact frozen candidate |
| 11 | RELEASE / PROD_GATE | Rollback is ready and `PROD_GO <candidate-ref>` is durably recorded |
| 12 | PROD_DEPLOY / PROD_SMOKE | Exact approved candidate is deployed and smoke-validated |
| 13 | CLOSURE | Release record is complete and work closes |

A project may use `APPROVE_TRANSFER <ref>` as an explicit boundary between approved Requirement and Development Analysis. If enabled, it is an additional control but does not replace Requirement Approval or Task Contract Approval.

## 3. Process modes

### AGENTFLOW

Default for new work.

### LEGACY-ADAPTED

Optional transition mode for work materially started under an older process.

Rules:

- a work item does not change process silently;
- conversion requires explicit approval;
- both modes may temporarily coexist;
- all production promotion should converge on one release lifecycle.

If no legacy transition exists, remove `LEGACY-ADAPTED` from the project adapter.

## 4. Canonical work-item header

```text
Process: AGENTFLOW | LEGACY-ADAPTED | INHERIT-PARENT
Phase: <canonical phase>
Status: <canonical status>
Blocked by: <reference or NONE>
```

The current canonical header takes precedence over historical wording elsewhere in the work item.

Document lifecycle metadata such as `CURRENT`, `SUPERSEDED`, `HISTORICAL`, or template status is **not** a work-item Phase/Status and must not be substituted for the canonical workflow taxonomy.

## 5. Canonical phases and statuses

| Phase | Canonical statuses |
|---|---|
| REQUIREMENTS | IDEA, REQUIREMENT_ANALYSIS, REQUIREMENT_READY_FOR_APPROVAL, REQUIREMENT_APPROVED, REQUIREMENT_CHANGES_REQUIRED, REQUIREMENT_DEFERRED, REQUIREMENT_REJECTED |
| ARCHITECTURE | ARCHITECTURE_REVIEW, ARCHITECTURE_READY_FOR_APPROVAL, ARCHITECTURE_APPROVED, ARCHITECTURE_CHANGES_REQUIRED, ARCHITECTURE_BLOCKED |
| DEVELOPMENT_ANALYSIS | DEVELOPMENT_ANALYSIS, DEVELOPMENT_ANALYSIS_BLOCKED, READY_FOR_TASK_CONTRACTS |
| TASK_CONTRACT | TASK_CONTRACT_DRAFT, TASK_CONTRACT_PROPOSED, TASK_CONTRACT_CHANGES_REQUIRED, TASK_CONTRACT_APPROVED |
| IMPLEMENTATION | IMPLEMENTATION_AUTHORIZED, IMPLEMENTING, IMPLEMENTATION_BLOCKED, IMPLEMENTATION_FAILED, IMPLEMENTATION_COMPLETE |
| EVIDENCE | EVIDENCE_PREPARING, EVIDENCE_READY, EVIDENCE_INCOMPLETE |
| REVIEW | REVIEW_PENDING, REVIEW_IN_PROGRESS, REVIEW_PASS, REVIEW_FAIL, REVIEW_BLOCKED |
| DEV | DEV_PENDING, DEV_IN_PROGRESS, DEV_PASS, DEV_FAIL, DEV_BLOCKED |
| CANDIDATE | CANDIDATE_READY, CANDIDATE_FROZEN, CANDIDATE_INVALIDATED |
| TEST | TEST_PENDING, TEST_IN_PROGRESS, TEST_PASS, TEST_FAIL, TEST_BLOCKED |
| RELEASE | RELEASE_PENDING, RELEASE_READY, RELEASE_BLOCKED |
| PROD_GATE | PROD_GO_PENDING, PROD_GO, PROD_NO_GO |
| PROD_DEPLOY | PROD_DEPLOYING, PROD_DEPLOYED, PROD_DEPLOY_FAILED |
| PROD_SMOKE | PROD_SMOKE_PENDING, PROD_SMOKE_PASS, PROD_SMOKE_FAIL, PROD_SMOKE_BLOCKED |
| CLOSURE | DONE, DEFERRED, CANCELLED, SUPERSEDED |

`BLOCKED` alone is not a canonical status. Use the phase-specific status and `Blocked by`.

## 6. Explicit approvals

Approvals are scoped and do not propagate to later gates.

Canonical tokens:

| Token | Authorizes | Does not authorize |
|---|---|---|
| `APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>` | persistence/activation of the approved AgentFlow Project Adapter/configuration | application implementation, infrastructure mutation, PROD |
| `APPROVE_REQUIREMENT <ref>` | approval of the exact Requirement | architecture choice, implementation, TEST, PROD |
| `APPROVE_TRANSFER <ref>` | entry into Development Analysis when the project enables a transfer gate | implementation, TEST, PROD |
| `APPROVE_ARCHITECTURE <ref>` | the referenced architecture decision | implementation or release |
| `APPROVE_TASK_CONTRACT <ref>` | implementation of that exact ATC | other ATCs, scope expansion, TEST, PROD |
| `APPROVE_PROD_DATA_USE <ref>` | explicitly bounded use of production data in non-PROD under approved minimisation/anonymisation controls | unrestricted copying, persistence beyond approved scope |
| `APPROVE_FORWARD_FIX <ref>` | bounded forward-fix path after rollback is proven infeasible | unrelated production changes or bypass of reconciliation/evidence |
| `PROD_GO <candidate-ref>` | promotion of the exact approved candidate | a changed candidate or new production mutation |

Generic phrases such as `continue`, `go`, `merge`, `looks good`, or `ok` do not replace a required explicit approval token.

### 6.1 Durable approval record

An approval changes workflow authorization only when it is recorded in the project-configured **durable approval record**.

A valid approval record contains at least:

- approval token;
- exact approved reference;
- approver identity;
- recorded timestamp;
- durable record reference or URL/ID.

A transient chat message may be the source of an owner decision, but the workflow must not transition on that approval until it is copied or mirrored into the configured durable record.

The Project Adapter defines the durable approval system/location. Core does not require a specific issue tracker or source-control platform.

## 7. Source-of-truth hierarchy

Each project must define canonical sources and their precedence.

Recommended model:

- Architecture → technical boundaries and approved target structure;
- Governance → decision, phase/status and approval rules;
- Delivery Lifecycle → DEV/TEST/PROD promotion rules;
- Requirements → approved product intent;
- Data/API contracts → stable interfaces;
- Repository → current implementation state;
- operational runbooks → procedures, not architecture;
- analyses/history → decision evidence, not current-state authority.

Conversation history, AI memory, and local copies are context, not technical source of truth.

## 8. Artifact identity and traceability

AgentFlow artifacts use stable typed identifiers and mandatory parent links as defined in `ARTIFACT-TRACEABILITY.md`.

Static identity/link rules are Core in v1.2. Automated artifact-graph validation is explicitly deferred to the future executable framework architecture.

## 9. Architecture policy

Material architecture changes require an Architecture Gate and explicit approval before implementation.

Typical triggers:

- datastore or persistence mechanism;
- source-of-truth or data ownership;
- authentication/authorization/tenancy;
- component boundaries;
- shared API/contracts;
- scheduler/orchestration/concurrency;
- provider/runtime/framework with architectural role;
- security/privacy/secrets model;
- material cost or portability/exit impact.

## 10. Implementation Preservation Rule

Approval of a feature or fix authorizes only the changes required for the approved outcome.

It does not implicitly authorize changes to component boundaries, APIs/contracts, persistence, identity/security, orchestration, providers/frameworks, dependencies, or established algorithms/semantics.

A materially different implementation mechanism is a separate change request unless already covered by the approved Architecture Gate.

## 11. No Opportunistic Refactoring

Do not use an approved feature or bugfix as authority for unrelated cleanup, redesign, reorganization, or refactoring.

If a larger refactor is necessary to implement the approved change safely, document its necessity and impact and obtain approval before execution.

## 12. Definition of Done

A change is not complete merely because code exists.

For work requiring production release, DONE normally requires:

- approved Requirement;
- approved scope;
- approved ATC;
- implementation complete;
- mandatory checks supported by the minimum evidence strength required by Core/project policy;
- Evidence Bundle complete;
- Independent Review pass bound to the exact candidate that proceeds;
- DEV pass;
- complete Candidate Manifest;
- immutable candidate frozen;
- TEST pass on that exact candidate;
- rollback prepared or an explicitly authorized forward-fix path when rollback is demonstrably infeasible;
- explicit production authorization for that exact candidate;
- exact candidate deployed;
- smoke pass;
- material documentation updated;
- Release Record complete.
