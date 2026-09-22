# AgentFlow Governance

Status: `REFERENCE CORE`
Version: `1.0.0`

## 1. Decision model

The project has one or more authorized human approvers. AI agents may analyze, recommend, execute approved work, and provide evidence, but they do not silently assume authority over material scope, architecture, security, privacy, cost, or production release decisions.

Nominal flow:

```text
Ideas / Requirements
→ Requirement Analysis
→ explicit Requirement Approval
→ Architecture Gate, when triggered
→ Development Analysis
→ Agent Task Contract
→ explicit Task Contract Approval
→ Implementation
→ Evidence
→ Independent Review
→ DEV → TEST → PROD lifecycle
```

There is no automatic transition from discussion to implementation.

## 2. Process modes

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

## 3. Canonical work-item header

```text
Process: AGENTFLOW | LEGACY-ADAPTED | INHERIT-PARENT
Phase: <canonical phase>
Status: <canonical status>
Blocked by: <reference or NONE>
```

The current canonical header takes precedence over historical wording elsewhere in the work item.

## 4. Canonical phases and statuses

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

## 5. Explicit approvals

Approvals are scoped and do not propagate to later gates.

Recommended tokens:

| Token | Authorizes | Does not authorize |
|---|---|---|
| `APPROVE_TRANSFER <ref>` | entry into Development Analysis | implementation, TEST, PROD |
| `APPROVE_ARCHITECTURE <ref>` | the referenced architecture decision | implementation or release |
| `APPROVE_TASK_CONTRACT <ref>` | implementation of that exact ATC | other ATCs, scope expansion, TEST, PROD |
| `PROD_GO <candidate-ref>` | promotion of the exact approved candidate | a changed candidate or new production mutation |

Generic phrases such as `continue`, `go`, `merge`, `looks good`, or `ok` do not replace a required explicit approval token.

## 6. Source-of-truth hierarchy

Each project must define canonical sources and their precedence.

Recommended model:

- Architecture → technical boundaries and approved target structure;
- Governance → decision and control rules;
- Delivery Lifecycle → DEV/TEST/PROD promotion rules;
- Requirements → approved product intent;
- Data/API contracts → stable interfaces;
- Repository → current implementation state;
- operational runbooks → procedures, not architecture;
- analyses/history → decision evidence, not current-state authority.

Conversation history, AI memory, and local copies are context, not technical source of truth.

## 7. Architecture policy

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

## 8. Implementation Preservation Rule

Approval of a feature or fix authorizes only the changes required for the approved outcome.

It does not implicitly authorize changes to:

- component boundaries;
- APIs/contracts;
- persistence;
- identity/security;
- orchestration;
- providers/frameworks;
- dependencies;
- established algorithms or semantics.

A materially different implementation mechanism is a separate change request unless already covered by the approved Architecture Gate.

## 9. No Opportunistic Refactoring

Do not use an approved feature or bugfix as authority for unrelated cleanup, redesign, reorganization, or refactoring.

If a larger refactor is necessary to implement the approved change safely, document its necessity and impact and obtain approval before execution.

## 10. Definition of Done

A change is not complete merely because code exists.

For work requiring production release, DONE normally requires:

- approved scope;
- implementation complete;
- mandatory tests pass;
- Evidence Bundle complete;
- Independent Review pass;
- DEV pass;
- immutable candidate frozen;
- TEST pass on that exact candidate;
- rollback prepared;
- explicit production authorization;
- exact candidate deployed;
- smoke pass;
- material documentation updated;
- Release Record complete.
