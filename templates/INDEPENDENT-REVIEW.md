# Independent Review

Template status: `CANONICAL`  
Framework compatibility: `1.1.1`

## Identity

- Review reference:
- ATC:
- Exact candidate ID:
- Candidate source / PR / commit:
- Evidence Bundle:
- Reviewer:
- Durable review record reference:

## Review rule

Review the exact implementation candidate against the exact approved ATC and the Evidence Bundle for that same candidate.

Do not modify the implementation during this review.

This verdict is valid **only** for the exact candidate ID above. Any implementation mutation creates a different candidate and invalidates this verdict for promotion.

## Contract conformance

| Area | Result | Notes / evidence |
|---|---|---|
| Objective | PASS / FAIL / BLOCKED | |
| Scope | PASS / FAIL / BLOCKED | |
| Out of scope preserved | PASS / FAIL / BLOCKED | |
| Acceptance criteria | PASS / FAIL / BLOCKED | |
| Required tests | PASS / FAIL / BLOCKED | |
| Architecture compliance | PASS / FAIL / BLOCKED | |
| Security/privacy constraints | PASS / FAIL / BLOCKED | |
| Evidence completeness | PASS / FAIL / BLOCKED | |
| Candidate identity verified | PASS / FAIL / BLOCKED | |

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

Use `REVIEW_FAIL` for demonstrated non-conformance/defect.

Use `REVIEW_BLOCKED` when required validation cannot be completed because evidence, access, environment, or dependency is missing.

## Invalidation rule

If implementation content changes after this verdict:

- retain this record as history;
- establish the new candidate identity;
- produce/update evidence for that candidate;
- perform a new Independent Review.
