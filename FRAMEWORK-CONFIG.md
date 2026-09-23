# Framework Configuration

Status: `REFERENCE CORE`  
Document version: `1.2.0`  
Framework compatibility: `1.2.x`

Use this document when adopting AgentFlow in a new project.

## 1. Configuration layering and precedence

AgentFlow uses two project-specific configuration artifacts:

### Project Adapter

Human-readable mapping, rationale, local conventions, exceptions, and ownership.

### agentflow.config.yaml

Authoritative source for **machine-readable project values**.

Rules:

1. Core safety/authority rules win unless an explicitly approved framework deviation exists.
2. Project Adapter explains the project mapping and rationale.
3. `agentflow.config.yaml` is authoritative for values consumed by automation/tools.
4. Any value represented in both Adapter and config must match.
5. A mismatch is a bootstrap/revalidation blocker until resolved.
6. Convenience documentation never overrides Core, Adapter, or config.

v1.2 defines this schema but does not provide a generic enforcement engine.

## 2. Project identity

Define:

- project name / namespace;
- repository/repositories or equivalent change system;
- owner / authorized approver model;
- main delivery process;
- legacy transition flag;
- compatible AgentFlow framework version/range;
- delivery model;
- immutable candidate identity mechanism.

## 3. Applicability preconditions

Before `READY_TO_ADOPT`, establish:

1. a durable project/change record;
2. a durable approval record;
3. an immutable or equivalently verifiable candidate/artifact identity;
4. a review mechanism;
5. inspectable delivery tooling/state sufficient to verify the above.

If any cannot be established, bootstrap returns `BLOCKED`.

For low-code/SaaS/store-distributed or non-git delivery, define an equivalent immutable snapshot/export/package/hash identifier.

## 4. Environments and access

Map AgentFlow roles to real environments and declare phase-scoped access.

For each phase define:

- reachable environments;
- credential/access-role reference;
- whether mutation is allowed.

Default: implementation phases have no PROD mutation access.

Never store credential secrets in AgentFlow configuration.

## 5. Work tracking and durable records

Define durable locations for:

- Requirements;
- Architecture Decisions;
- Development Analyses;
- ATCs;
- Evidence Bundles;
- Independent Reviews;
- Candidate Manifests;
- Release Records;
- approvals.

References must be stable and resolvable.

## 6. Approval tokens

Canonical defaults:

```text
APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>
APPROVE_REQUIREMENT <ref>
APPROVE_TRANSFER <ref>             # only if project enables transfer gate
APPROVE_ARCHITECTURE <ref>
APPROVE_TASK_CONTRACT <ref>
APPROVE_PROD_DATA_USE <ref>
APPROVE_FORWARD_FIX <ref>
PROD_GO <candidate-ref>
```

A project may rename tokens in its Adapter/config, but approval must remain explicit, scoped, non-ambiguous, and durably recorded.

## 7. Gates

Machine-readable config should represent whether these gates are required/enabled:

- bootstrap activation;
- Requirement Approval;
- optional Transfer;
- Architecture Gate on trigger;
- ATC Approval;
- Evidence readiness;
- Independent Review;
- DEV verification;
- Candidate Manifest/freeze;
- TEST;
- PROD GO;
- smoke/closure.

## 8. Architecture triggers

Start with Core triggers and add project-specific triggers.

## 9. Execution limits

Define:

- per-execution retry limit;
- cross-cycle remediation budget;
- single-active-executor requirement;
- handoff record location.

## 10. Evidence

Define project evidence defaults.

Core minimum:

- mandatory checks require `ARTIFACT` or `REPRODUCIBLE`;
- `ATTESTED` alone cannot satisfy a mandatory check.

Projects may require stronger proof.

## 11. Independent Review

Define:

- minimum independence level: `IR1_FRESH_CONTEXT | IR2_DISTINCT_REVIEWER | IR3_ORGANIZATIONAL`;
- candidate identity binding mechanism;
- durable review record location.

Core minimum is `IR1_FRESH_CONTEXT`.

## 12. Release / recovery

Define:

- candidate identity;
- Candidate Manifest location;
- rollback mechanism;
- backup/restore requirements;
- forward-fix enablement/policy;
- hotfix path.

## 13. Production-data handling

Define:

- whether production data may ever enter non-PROD;
- approval record required;
- anonymisation/minimisation standard;
- retention/deletion control.

Default: prohibited.

## 14. Revalidation

Project Adapter/config must record:

- last validated timestamp/date;
- framework version last validated against;
- revalidation triggers;
- outstanding gaps with owner and closure condition.

Minimum revalidation triggers:

- environment topology change;
- source-control/change-system change;
- CI/CD or deployment mechanism change;
- owner/approval model change;
- durable approval-record change;
- candidate identity mechanism change;
- phase credential/access-boundary change;
- AgentFlow framework version outside declared compatible range.

## 15. Metrics / gate expectations

Projects may define optional gate response expectations and metric collection settings using `METRICS.md`.

Expiry of a response expectation never authorizes an automatic transition.
