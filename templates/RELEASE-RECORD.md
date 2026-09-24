# Release Record

Template status: `CANONICAL`  
Template version: `1.3.0`  
Framework compatibility: `1.3.x`

## Identity / traceability
- Release ID: `REL-<n>`
- Candidate Manifest ID:
- Exact promoted candidate ID:

## Included work trace
| Requirement | DA | ATC | Evidence | Review | Candidate Manifest entry |
|---|---|---|---|---|---|
| | | | | | |

## Environment transition readiness

For every affected persistent target environment classify:
- `ALREADY_COMPLIANT`
- `TRUSTED_BOOTSTRAP`
- `APPROVED_TRANSITION_READY`
- `BLOCKED`

| Environment | Classification | Transition/bootstrap proof | Open blocker |
|---|---|---|---|
| | | | |

Any affected target classified `BLOCKED` makes release status `RELEASE_BLOCKED` before PROD_GO. This is a readiness condition, not a new approval gate.

## DEV / candidate freeze
- DEV PASS evidence:
- Candidate Manifest complete:
- Candidate identity/composition verified:
- Freeze reference:

## TEST
- TEST PASS evidence:
- Candidate identity verified:

## Previous production state
- Previous PROD identity:
- Previous config/data reference, if relevant:

## Recovery
- Rollback action/reference:
- Backup/restore proof, if required:
- Rollback feasible: YES / NO
- If NO, forward-fix reference/approval:

## Production authorization
- PROD GO token/reference:
- Durable approval record:
- Approved by:
- Timestamp:

## Deployment / smoke
- Deployed candidate ID:
- Deployment evidence:
- Smoke result: `PROD_SMOKE_PASS | PROD_SMOKE_FAIL | PROD_SMOKE_BLOCKED`
- Smoke evidence:

## Final status
`DONE | ROLLED_BACK | BLOCKED`

Do not invent workflow statuses outside `GOVERNANCE.md`.
