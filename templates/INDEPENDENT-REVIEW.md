# Independent Review

Template status: `CANONICAL`  
Template version: `1.2.0`  
Framework compatibility: `1.2.x`

## Identity / traceability

- Review ID: `REV-<atc>-<seq>`
- Parent ATC:
- Evidence Bundle:
- Exact reviewed candidate ID:
- Candidate source / PR / change reference:
- Durable review record reference:

## Reviewer identity / independence

- Reviewer:
- Actor type: `HUMAN | AI | HYBRID`
- Agent/tool:
- Model/version:
- Session/run reference:
- Independence level: `IR1_FRESH_CONTEXT | IR2_DISTINCT_REVIEWER | IR3_ORGANIZATIONAL`
- Project-required minimum:

`IR0_SELF` is not a valid Independent Review.

## Review rule

Review the exact implementation candidate against the exact approved ATC and the Evidence Bundle for that same candidate.

Do not modify the implementation during this review.

This verdict is valid only for the exact candidate ID above.

## Evidence sufficiency

For each mandatory ATC check verify:

- evidence class is ARTIFACT or REPRODUCIBLE;
- stable evidence reference is present;
- result supports the claimed acceptance outcome.

If any mandatory check is supported only by ATTESTED evidence, verdict must be `REVIEW_BLOCKED`.

## Contract conformance

| Area | Result | Notes / evidence |
|---|---|---|
| Objective | PASS / FAIL / BLOCKED | |
| Scope | PASS / FAIL / BLOCKED | |
| Out of scope preserved | PASS / FAIL / BLOCKED | |
| Acceptance criteria | PASS / FAIL / BLOCKED | |
| Mandatory checks / evidence class | PASS / FAIL / BLOCKED | |
| Architecture compliance | PASS / FAIL / BLOCKED | |
| Security/privacy constraints | PASS / FAIL / BLOCKED | |
| Candidate identity verified | PASS / FAIL / BLOCKED | |
| Review independence satisfied | PASS / FAIL / BLOCKED | |

## Findings

### Blocking findings

- 

### Non-blocking findings

- 

## Verdict

Choose exactly one:

- `REVIEW_PASS`
- `REVIEW_FAIL`
- `REVIEW_BLOCKED`

## Invalidation rule

If implementation content changes after this verdict:

- retain this record as history;
- establish the new candidate identity;
- produce/update evidence for that candidate;
- perform a new Independent Review.
