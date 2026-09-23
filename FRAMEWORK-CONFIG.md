# Framework Configuration

Status: `REFERENCE CORE`  
Version: `1.1.1`

Use this document when adopting AgentFlow in a new project.

## 1. Project identity

Define:

- Project name
- Repository/repositories
- Product owner or authorized approver
- Main delivery process: `AGENTFLOW`
- Legacy transition required: `YES | NO`
- Compatible AgentFlow framework version/range

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

## 4. Work tracking and durable records

Define where these artifacts live:

- Requirement;
- Architecture Gate / ADR;
- Development Analysis;
- Agent Task Contract;
- Evidence Bundle;
- Independent Review verdict;
- Release Record.

Also define the **durable approval record location** used for scoped approvals. It may be the same work tracker or another system, but approval references must be stable, inspectable, and linkable.

## 5. Approval tokens

Canonical defaults:

```text
APPROVE_REQUIREMENT <ref>
APPROVE_TRANSFER <ref>        # only if project enables transfer gate
APPROVE_ARCHITECTURE <ref>
APPROVE_TASK_CONTRACT <ref>
PROD_GO <candidate-ref>
```

A project may rename tokens in its Project Adapter, but approval must remain explicit, scoped, non-ambiguous, and durably recorded.

## 6. Architecture triggers

Start with the Core triggers from `AGENTFLOW.md` and add project-specific triggers where required.

## 7. Retry defaults

Recommended default:

```text
Implementation self-correction: 2 cycles
Review remediation: new implementation cycle
TEST failure: return to DEV and create new candidate
```

A specific ATC may define another per-execution retry limit.

## 8. Required evidence

Choose project defaults for the checks relevant to that project.

Evidence integrity classes are not standardized in v1.1.1.

## 9. Review binding

Define the candidate identity format used by Independent Review.

Core requirement:

- every review verdict records one exact candidate identity;
- if implementation changes, the old verdict is historical only and a new review is required.

## 10. Release identity

Define the canonical candidate identifier.

Recommended:

`CANDIDATE_ID = immutable source commit SHA`

Alternative immutable artifacts are allowed if the project cannot promote source identity directly.

## 11. Rollback policy

Define minimum rollback evidence for:

- code;
- configuration;
- database/schema/data;
- infrastructure;
- third-party configuration.

## 12. Documentation map

Define canonical homes for:

- Architecture;
- Governance;
- Requirements;
- Data/API contracts;
- Operations;
- AI execution rules.

Avoid two current sources of truth for the same subject.

## 13. Precedence

When a local configuration value conflicts with Core:

1. Core safety/authority rules win unless an explicitly approved framework deviation exists;
2. Project Adapter defines project-specific mapping and allowed customization;
3. machine-readable config implements the Adapter values;
4. convenience documentation never overrides Core or the Adapter.
