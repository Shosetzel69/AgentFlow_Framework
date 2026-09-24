# Framework Configuration

Status: `REFERENCE CORE`  
Document version: `1.3.0`  
Framework compatibility: `1.3.x`

Use this document when adopting or revalidating AgentFlow.

## 1. Layering and precedence

Project Adapter is the human-readable mapping/rationale. `agentflow.config.yaml` is authoritative for machine-readable project values.

Core safety/authority rules win unless an approved framework deviation exists. Any overlapping Adapter/config value must match. Convenience documentation never overrides Core/Adapter/config.

AgentFlow v1.3 defines configuration semantics but no generic runtime enforcement engine.

## 2. Applicability

Before `READY_TO_ADOPT`, establish:
1. durable project/change record;
2. durable approval record;
3. immutable/equivalently verifiable candidate identity;
4. review mechanism;
5. inspectable delivery state.

Non-git delivery may use immutable snapshot/export/package/hash identity.

## 3. Project identity and records

Define project namespace, delivery model, compatible AgentFlow range and immutable candidate identity.

Map durable locations for:
- Requirements / ADR / Development Analysis / ATCs;
- Evidence / Independent Review / Candidate Manifest / Release Record;
- approvals;
- completed stage results;
- material analysis checkpoints.

A project may reuse its canonical work-item/stage-result record for checkpoints; Core does not require a new store.

## 4. Environments and access

Map DEV/TEST/PROD and phase-scoped environment/credential roles. Implementation phases default to no PROD mutation access. Never store secrets in configuration.

## 5. Approval and gates

Map canonical approval tokens and enabled project gates permitted by Core.

Project config does not create a new gate merely by naming a preference. Gate authority follows `GOVERNANCE.md`.

## 6. Execution policy

Define:
- retry limit;
- remediation-cycle budget;
- single-active-executor/handoff location;
- execution-context policy values where the project overrides/extends Core defaults.

Normal execution uses the approved ATC + applicable `AI-EXECUTION-RULES.md` + declared project/source context. Configuration must not turn context budgeting into a runtime engine unless separately architected.

Recommended project fields:
- controlled-context primary measure: characters/bytes;
- normal estimated-token target;
- stretch target;
- full-document reads exceptional: YES;
- default semantic exclusions or project additions.

## 7. Evidence policy

For mandatory checks choose an explicit sufficiency policy:
- `ARTIFACT_OR_REPRODUCIBLE`
- `ARTIFACT_REQUIRED`
- `REPRODUCIBLE_REQUIRED`
- `BOTH_REQUIRED`

ATTESTED alone is never sufficient.

Map evidence retention and stable-reference expectations.

## 8. Independent / external review

Define:
- minimum IR level (`IR1_FRESH_CONTEXT` or stronger);
- candidate identity binding;
- durable review-record location;
- external reviewer write/access boundary.

External-review authority may be limited to durable review records and never implies implementation mutation authority.

## 9. Environment transition readiness

If approved architecture changes persistent invariants, project mapping identifies affected target environments and transition/bootstrap proof needed for:
- `ALREADY_COMPLIANT`
- `TRUSTED_BOOTSTRAP`
- `APPROVED_TRANSITION_READY`
- `BLOCKED`

A BLOCKED affected target yields RELEASE_BLOCKED before PROD_GO.

## 10. Release / recovery and data

Define candidate manifest, rollback/backup, forward-fix/hotfix path and production-data handling.

Production data in non-PROD remains prohibited by default unless the explicit Core exception is satisfied.

## 11. Revalidation

Record last validated version/date and revalidate after environment/toolchain/owner/approval-record/candidate-identity/access changes or incompatible framework version.

Adopting v1.3 from v1.2 requires explicit Adapter/config revalidation; no consuming project auto-upgrades.

## 12. Metrics

Projects may collect `METRICS.md` manually or with project tooling. Execution-context telemetry must keep AgentFlow-controlled overhead separate from source/code exploration.

Reference-scenario regression is a framework-release concern; projects need not implement automated benchmark tooling.
