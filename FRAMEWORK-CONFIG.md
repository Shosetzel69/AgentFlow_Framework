# Framework Configuration

Use this document once when adopting AgentFlow in a new project.

## 1. Project identity

Define:

- Project name
- Repository/repositories
- Product owner or authorized approver
- Main delivery process: `AGENTFLOW`
- Legacy transition required: `YES | NO`

## 2. Environments

Map the framework roles to real environments:

| Framework role | Project environment |
|---|---|
| DEV | `<value>` |
| TEST | `<value>` |
| PROD | `<value>` |

Optional environments such as staging, preview, sandbox, or disaster-recovery are project adapters. They must not weaken the immutable-candidate rule.

## 3. Source control

Define:

- default protected branch;
- development branch convention;
- pull/merge request requirement;
- direct-write policy;
- immutable candidate identifier, usually commit SHA;
- merge strategy that preserves tested candidate identity.

## 4. Issue tracking

Define where these artifacts live:

- Requirement
- Architecture Gate
- Development Analysis
- Agent Task Contract
- Evidence Bundle
- Review verdict
- Release Record

They may live in one issue tracker or multiple tools, but references must be stable and linkable.

## 5. Approval tokens

Recommended defaults:

```text
APPROVE_TRANSFER <ref>
APPROVE_ARCHITECTURE <ref>
APPROVE_TASK_CONTRACT <ref>
PROD_GO <candidate-ref>
```

A project may rename them, but approval must remain explicit, scoped, and non-ambiguous.

## 6. Architecture triggers

Start with the Core triggers from `AGENTFLOW.md` and add project-specific triggers where required.

Examples:

- regulated-data boundary;
- cryptographic architecture;
- event schema compatibility;
- public API versioning;
- mobile-store release model;
- ML model governance;
- infrastructure cost threshold.

## 7. Retry defaults

Recommended default:

```text
Implementation self-correction: 2 cycles
Review remediation: new implementation cycle
TEST failure: return to DEV and create new candidate
```

A specific ATC may define another retry limit.

## 8. Required evidence

Choose project defaults for:

- unit tests;
- integration tests;
- static analysis;
- build;
- deployment checks;
- screenshots;
- logs;
- database migration proof;
- security tests;
- performance evidence.

Only evidence materially relevant to the task should be mandatory.

## 9. Release identity

Define the canonical candidate identifier.

Recommended:

```text
CANDIDATE_ID = immutable source commit SHA
```

Alternative immutable artifacts are allowed if the project cannot promote source identity directly.

## 10. Rollback policy

Define minimum rollback evidence for:

- code;
- configuration;
- database/schema/data;
- infrastructure;
- third-party configuration.

## 11. Documentation map

Define canonical homes for:

- Architecture
- Governance
- Requirements
- Data/API contracts
- Operations
- AI execution rules

Avoid two current sources of truth for the same subject.
