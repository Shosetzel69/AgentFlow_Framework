# Evidence Bundle

Template status: `CANONICAL`  
Template version: `1.3.0`  
Framework compatibility: `1.3.x`

## Identity / traceability
- Evidence ID: `EV-<atc>-<seq>`
- Parent ATC:
- Parent Requirement:
- Exact candidate ID:
- Candidate branch / PR / change reference:

## Executor provenance
- Actor type: `HUMAN | AI | HYBRID`
- Executor identity/reference:
- Agent/tool:
- Model/version:
- Session/run reference:
- Credential/access-role reference:

Never record credential secrets.

## Execution-rules provenance
- Execution rules: `AI-EXECUTION-RULES.md`
- Document version used:
- Framework version/range:

## AgentFlow-controlled context telemetry

This telemetry excludes implementation-driven source/code exploration.

- Declared pre-execution controlled context (chars/bytes):
- Declared estimated tokens:
- Actual initial controlled context (chars/bytes):
- Context expansion (chars/bytes):
- Largest controlled read (chars/bytes):
- Full-document reads (count / chars):
- Total controlled context (chars/bytes):
- Informational estimated tokens:
- Deviations from declared context:

Telemetry is evidence/measurement, not retroactive execution authorization.

## Files / components changed
-

## Tests / checks

Evidence classes:
- `ATTESTED` — statement only;
- `ARTIFACT` — persisted/externally produced output with stable reference;
- `REPRODUCIBLE` — reviewer-rerunnable verification with recorded inputs.

Evidence policies:
- `ARTIFACT_OR_REPRODUCIBLE`
- `ARTIFACT_REQUIRED`
- `REPRODUCIBLE_REQUIRED`
- `BOTH_REQUIRED`

| Check | Mandatory | Result | Required policy | Evidence class(es) | Stable reference / rerun command | Independently reproducible |
|---|---|---|---|---|---|---|
| | YES / NO | PASS / FAIL / BLOCKED / N/A | | | | YES / NO / PARTIAL |

`ATTESTED` alone never satisfies a mandatory check.

Prefer stable references to evidence over embedding large logs/content when a durable reference exists.

## Acceptance criteria mapping
| Acceptance criterion | Status | Evidence reference |
|---|---|---|
| AC-1 | PASS / FAIL / BLOCKED | |

## Assumptions / deviations / limitations / residual risks
- Assumptions:
- Deviations:
- Known limitations:
- Residual risks:

## Retry / remediation history
- Current implementation cycle:
- Self-correction cycles used:
- Remediation cycle count:
- Trigger for current remediation, if any:

## Artifact status
Choose only:
- `EVIDENCE_READY`
- `EVIDENCE_INCOMPLETE`

This bundle describes only the exact candidate above. Changed implementation content requires evidence for the new candidate before review.
