# AgentFlow Project Adapter

Template status: `CANONICAL`  
Template version: `1.2.0`  
Framework compatibility: `1.2.x`

Project:
Project namespace:
Adapter version:
Framework version/range: `>=1.2.0,<2.0.0`
Last validated:
Validated framework version:
Delivery model:

## 1. Ownership / approvals

- Owner model: `single_owner | multi_approver`
- Requirement approver:
- Architecture approver:
- Task Contract approver:
- PROD approver:
- Forward-fix approver:
- Production-data-use approver:

### Durable approval record

- System:
- Location / project namespace:
- Stable reference format:
- Required approver identity format:

An approval is workflow-effective only after it is recorded here according to Core Governance.

## 2. Toolchain / durable records

- Source/change control:
- Issue/work tracker:
- CI:
- CD:
- Runtime/cloud:
- Database:
- Observability:
- Secrets/access manager:
- AI agents:
- Requirement record location:
- ADR location:
- Development Analysis location:
- ATC location:
- Evidence location:
- Review location:
- Candidate Manifest location:
- Release Record location:

## 3. Artifact identity mapping

- AgentFlow typed-ID scheme: `native | AgentFlow default | custom equivalent`
- Requirement ID mapping:
- ADR ID mapping:
- DA ID mapping:
- ATC ID mapping:
- Evidence ID mapping:
- Review ID mapping:
- Candidate Manifest ID mapping:
- Release ID mapping:

All mappings must preserve stable typed identity and mandatory parent links from `ARTIFACT-TRACEABILITY.md`.

## 4. Change/review rules

- Protected/default integration target:
- Branch/change naming:
- PR/MR/change review required: YES / NO
- Direct writes to protected target: YES / NO
- Integration strategy:
- Immutable candidate identity mechanism:

## 5. Environment mapping

| AgentFlow role | Project environment | Notes |
|---|---|---|
| DEV | | |
| TEST | | |
| PROD | | |

## 6. Phase-scoped access

Record role/reference only. Never store secrets.

| Phase | Reachable environments | Credential/access role | PROD mutation allowed |
|---|---|---|---|
| REQUIREMENTS | | | NO |
| ARCHITECTURE | | | NO |
| DEVELOPMENT_ANALYSIS | | | NO |
| IMPLEMENTATION | | | NO |
| EVIDENCE | | | NO |
| REVIEW | | | NO |
| TEST | | | NO |
| PROD_DEPLOY | | | YES / NO |

Implementation phases default to no PROD mutation access.

## 7. Approval tokens

```text
Bootstrap:
Requirement:
Transfer, if enabled:
Architecture:
Task Contract:
Production data use:
Forward fix:
PROD:
```

## 8. Architecture triggers added by this project

- 

## 9. Execution policy

- Per-execution retry limit:
- Remediation-cycle budget:
- Single active executor per ATC: YES / NO
- Handoff record location:

## 10. Evidence policy

- Mandatory-check minimum class: `ARTIFACT | REPRODUCIBLE`
- Additional artifact requirements:
- Evidence retention expectation:

## 11. Independent Review

- Required independence level: `IR1_FRESH_CONTEXT | IR2_DISTINCT_REVIEWER | IR3_ORGANIZATIONAL`
- Durable review record location:
- Candidate identity binding mechanism:

Core minimum: `IR1_FRESH_CONTEXT`.

## 12. Release / recovery

- Candidate Manifest location:
- Rollback mechanism:
- Database migration rule:
- Backup requirement:
- Forward-fix enabled: YES / NO
- Forward-fix reconciliation mechanism:
- Hotfix implementation path:

## 13. Production-data handling

- Production data allowed in non-PROD by default: NO
- Exception approval location:
- Required anonymisation/minimisation standard:
- Retention/deletion condition:

## 14. Canonical documentation map

| Subject | Canonical source |
|---|---|
| Architecture | |
| Governance | |
| Requirements | |
| Data/API contracts | |
| Operations | |
| AI execution rules | |

## 15. Revalidation

- Last validated:
- Validated framework version:
- Revalidation triggers:
  - environment topology change
  - source/change-control change
  - CI/CD/deployment change
  - owner/approval model change
  - approval-record location change
  - candidate identity mechanism change
  - phase access-boundary change
  - incompatible framework version
- Additional project trigger:

## 16. Outstanding gaps

| Gap | Owner | Temporary accepted condition | Closure condition | Revalidation/target |
|---|---|---|---|---|
| | | | | |

A READY_WITH_GAPS adoption cannot contain a gap without owner and closure condition.

## 17. Metrics / gate response expectations

- Metric collection: `manual | project-specific tooling | none`
- Requirement approval target:
- Architecture approval target:
- ATC approval target:
- Independent Review target:
- PROD GO target:

Targets are expectations only and never auto-authorize transitions.

## 18. Legacy transition

- Enabled: YES / NO
- Legacy work identification rule:
- Retirement condition:

## 19. Adapter/config consistency

Machine-readable values are authoritative in `agentflow.config.yaml`; this Adapter is authoritative for rationale and local mapping.

Any overlapping value must match. A material mismatch blocks adoption/revalidation.
