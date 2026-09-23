# AgentFlow Bootstrap Report

Template status: `CANONICAL`  
Template version: `1.2.0`  
Framework compatibility: `1.2.x`

Project:
Bootstrap date:
Bootstrap mode: `GREENFIELD | EXISTING | REVALIDATION`
Framework version: `1.2.0`
Last validated:
Executor:

## 1. Verdict

`READY_TO_ADOPT | READY_WITH_GAPS | BLOCKED`

Reason:

## 2. Applicability preconditions

| Precondition | Result | Evidence / mapping |
|---|---|---|
| Durable project/change record | PASS / FAIL / DECIDE | |
| Durable approval record | PASS / FAIL / DECIDE | |
| Immutable/equivalent candidate identity | PASS / FAIL / DECIDE | |
| Change-review mechanism | PASS / FAIL / DECIDE | |
| Inspectable delivery state/tooling | PASS / FAIL / DECIDE | |

Any unresolved FAIL/DECIDE that prevents an equivalent control yields `BLOCKED`.

## 3. Evidence baseline

- Repository/change systems:
- Default/protected target:
- Issue/work tracker:
- CI/CD:
- Environments:
- Architecture source:
- Requirements source:
- Durable approval record:
- Candidate identity mechanism:
- Release/deployment source:

## 4. Source-of-truth map

| Subject | Current source | Status | Notes |
|---|---|---|---|
| Requirements | | | |
| Architecture | | | |
| Data/API contracts | | | |
| Delivery process | | | |
| Approval records | | | |
| Artifact identity | | | |
| Release/deploy | | | |
| AI execution rules | | | |
| Operations | | | |

## 5. Environment / access map

| AgentFlow phase/role | Project environment | Credential/access role | PROD mutation |
|---|---|---|---|
| IMPLEMENTATION | | | NO |
| REVIEW | | | NO |
| TEST | | | NO |
| PROD_DEPLOY | | | YES / NO |

## 6. Gap matrix

Use: `EXISTS | ADAPT | ADD | DECIDE | BLOCKED`.

| AgentFlow control | Current project | Classification | Required action |
|---|---|---|---|
| Bootstrap approval | | | |
| Requirement approval | | | |
| Durable approval record | | | |
| Architecture Gate | | | |
| Development Analysis | | | |
| Agent Task Contract | | | |
| Retry + remediation budget | | | |
| Executor provenance/handoff | | | |
| Evidence class control | | | |
| Review independence level | | | |
| Candidate-bound review | | | |
| Candidate Manifest | | | |
| Immutable candidate | | | |
| Independent TEST | | | |
| Rollback / forward-fix | | | |
| PROD GO | | | |
| Production-data handling | | | |
| Phase access boundaries | | | |
| Artifact identity/parent links | | | |
| Progressive context | | | |

## 7. Outstanding gaps

| Gap | Owner | Temporary accepted condition | Closure condition | Target/revalidation trigger |
|---|---|---|---|---|
| | | | | |

No owner/closure condition => verdict cannot be `READY_WITH_GAPS`.

## 8. Generated artifacts

- PROJECT-ADAPTER.md: GENERATED / BLOCKED
- agentflow.config.yaml: GENERATED / BLOCKED

## 9. Revalidation

- Validated framework version:
- Last validated:
- Trigger causing this validation:
- Next revalidation triggers:

## 10. Adapter/config consistency

- Result: PASS / BLOCKED
- Mismatches:

## 11. Decisions required

1.

## 12. Assumptions / risks

- 

## 13. Mutations performed during bootstrap

Expected default: `NONE`.

- 

## 14. Owner gate

Expected command:

`APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>`

Durable approval record reference:
