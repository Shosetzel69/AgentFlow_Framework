# Evidence Bundle

Template status: `CANONICAL`  
Template version: `1.2.0`  
Framework compatibility: `1.2.x`

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

Do not record credential secrets.

## Files / components changed

- 

## Tests / checks

Evidence classes:

- `ATTESTED` — executor statement only;
- `ARTIFACT` — persisted/externally produced output with stable reference;
- `REPRODUCIBLE` — reviewer-rerunnable command/pipeline with recorded inputs.

| Check | Mandatory | Result | Evidence class | Artifact/reference or rerun command | Independently reproducible |
|---|---|---|---|---|---|
| | YES / NO | PASS / FAIL / BLOCKED / N/A | ATTESTED / ARTIFACT / REPRODUCIBLE | | YES / NO / PARTIAL |

Mandatory checks require ARTIFACT or REPRODUCIBLE proof.

## Acceptance criteria mapping

| Acceptance criterion | Status | Evidence reference |
|---|---|---|
| AC-1 | PASS / FAIL / BLOCKED | |

## Assumptions

- 

## Deviations

- None / 

## Known limitations

- 

## Residual risks

- 

## Retry / remediation history

- Current implementation cycle:
- Self-correction cycles used:
- Remediation cycle count:
- Trigger for current remediation, if any:

## Artifact status

Choose only a canonical EVIDENCE-phase status:

- `EVIDENCE_READY`
- `EVIDENCE_INCOMPLETE`

Implementation-phase statuses belong to the work item, not to this Evidence artifact.

This bundle describes only the exact candidate ID above. If implementation content changes, create/update evidence for the new candidate before review.
