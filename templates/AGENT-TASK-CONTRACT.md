# Agent Task Contract

Template status: `CANONICAL`  
Template version: `1.3.0`  
Framework compatibility: `1.3.x`

## Identity / traceability
- ATC ID: `ATC-<req>-<seq>`
- Parent Requirement:
- Parent Development Analysis:
- Relevant ADR(s):
- Process: `AGENTFLOW`
- Phase: `TASK_CONTRACT`
- Status: `TASK_CONTRACT_PROPOSED`

## Objective

## Scope
-

## Out of scope
-

## Execution Context

**Required control context**
- this exact approved ATC;
- applicable `AI-EXECUTION-RULES.md` version.

**Required project/source context**
- exact file/section/range:

**Optional expansion**
- exact source:
- named condition/question permitting load:

**Excluded**
- task-specific additions to Core defaults:

**Declared pre-execution size**
- characters/bytes:
- estimated tokens (informational):
- normal target <5k: PASS / EXCEPTION

Missing execution authority/rule is a STOP condition, not permission to explore Core/history. Missing project/source detail may use bounded targeted expansion.

## Candidate components / files
-

## Dependencies
-

## Constraints
-

## Acceptance criteria
Each criterion is independently verifiable.
- [ ]

## Mandatory tests / checks

Declare the sufficiency policy for each mandatory check.

| Check | Mandatory | Evidence policy |
|---|---|---|
| | YES / NO | ARTIFACT_OR_REPRODUCIBLE / ARTIFACT_REQUIRED / REPRODUCIBLE_REQUIRED / BOTH_REQUIRED |

ATTESTED alone never satisfies a mandatory check.

## Per-execution retry limit
Recommended default: `2 self-correction cycles`

## Cross-cycle remediation budget
Recommended default: `2 remediation cycles after the initial implementation cycle`

## Stop conditions
Use `AI-EXECUTION-RULES.md` plus task-specific additions:
-

## Execution ownership
- Active executor:
- Actor type: `HUMAN | AI | HYBRID`
- Agent/tool:
- Model/version:
- Session/run reference:
- Credential/access-role reference:

Only one active executor is allowed at a time.

### Handoff history
| From | To | Timestamp | Reason | Candidate/work state | Open blockers |
|---|---|---|---|---|---|
| | | | | | |

## Evidence required
- exact candidate identity;
- executor provenance;
- mandatory checks and evidence references;
- acceptance-criteria mapping;
- execution-rules version;
- AgentFlow-controlled context telemetry;
- assumptions/deviations/limitations/residual risks;
- retry/remediation history;
- branch/PR/change reference.

## Approval
Expected token:

```text
APPROVE_TASK_CONTRACT <ATC-ID>
```

Durable approval record:
- Approved by:
- Timestamp:
- Approval record reference:
