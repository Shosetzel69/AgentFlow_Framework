# Independent Review

Template status: `CANONICAL`  
Template version: `1.3.0`  
Framework compatibility: `1.3.x`

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
- Implementation executor identity/reference:
- Independence level: `IR1_FRESH_CONTEXT | IR2_DISTINCT_REVIEWER | IR3_ORGANIZATIONAL`
- Separation basis:
- Project-required minimum:
- Policy/config reference:

`IR0_SELF` does not satisfy Independent Review.

## Review rule

Review the exact candidate against the exact approved ATC and matching Evidence Bundle. Do not modify implementation in the same review activity.

This verdict is candidate-bound.

## Evidence sufficiency

For each mandatory check verify that evidence satisfies its declared policy:
- `ARTIFACT_OR_REPRODUCIBLE`
- `ARTIFACT_REQUIRED`
- `REPRODUCIBLE_REQUIRED`
- `BOTH_REQUIRED`

ATTESTED-only proof for a mandatory check => `REVIEW_BLOCKED`.

## Context-readiness / telemetry review
- Declared pre-execution size evidence present: YES / NO / N/A
- Actual controlled-context telemetry present: YES / NO
- AgentFlow-controlled context separated from source/code exploration: PASS / FAIL / BLOCKED
- Unexplained full-document/history/Core preload: NONE / FINDING

Telemetry does not replace authoring-time readiness evidence.

## Candidate composition / identity
- Exact candidate verified:
- Composition/equivalence proof, if used:
- Proof class/reference:
- Independently verifiable: YES / NO

If equivalence to a previously reviewed component/candidate cannot be independently verified, fresh evidence/review is required.

## Contract conformance
| Area | Result | Notes / evidence |
|---|---|---|
| Objective | PASS / FAIL / BLOCKED | |
| Scope / exclusions | PASS / FAIL / BLOCKED | |
| Acceptance criteria | PASS / FAIL / BLOCKED | |
| Mandatory evidence policy | PASS / FAIL / BLOCKED | |
| Architecture compliance | PASS / FAIL / BLOCKED | |
| Candidate identity/composition | PASS / FAIL / BLOCKED | |
| Context readiness/telemetry | PASS / FAIL / BLOCKED | |
| Review independence | PASS / FAIL / BLOCKED | |

## Findings
### Blocking
-
### Non-blocking
-

## Verdict
Choose exactly one:
- `REVIEW_PASS`
- `REVIEW_FAIL`
- `REVIEW_BLOCKED`

## Invalidation rule
Any implementation-content change retains this record as history but invalidates its verdict for the changed candidate. Establish a new candidate identity, evidence, and review.
