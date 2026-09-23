# AgentFlow Delivery Lifecycle — DEV → TEST → PROD

Status: `REFERENCE CORE`  
Version: `1.1.1`

## 1. Goal

The release process must answer at any time:

1. What change is being released?
2. What exact artifact or source identity was reviewed and tested?
3. What exact identity is running in production?
4. How do we return to the previous known-good state?

The normative end-to-end AgentFlow process is defined in `GOVERNANCE.md`. This document governs only release promotion.

## 2. Release flow

```text
reviewed implementation candidate
→ DEV verification
→ freeze same CANDIDATE_ID
→ TEST exact same candidate
→ TEST PASS
→ integrate/publish without identity rewrite
→ rollback preflight
→ explicit PROD GO for exact candidate
→ PROD exact same candidate
→ smoke PASS
→ close
```

Failure flow:

```text
candidate changes or TEST fails
→ invalidate affected review/test evidence
→ DEV remediation
→ new candidate identity
→ Evidence / Review as required
→ DEV verification
→ TEST again
```

## 3. Non-negotiable rules

1. The protected default branch is not a development or debugging environment.
2. Source changes use the project-approved change/review mechanism.
3. DEV is the normal implementation/debugging environment.
4. Independent Review verdicts are bound to one exact candidate identity.
5. Candidate mutation after `REVIEW_PASS` invalidates that review for promotion and requires a new review of the changed candidate.
6. TEST validates the exact frozen candidate.
7. Fixes are not made directly in TEST.
8. Any source change after candidate freeze creates a new candidate and invalidates the previous TEST result.
9. Merge/integration does not itself authorize production deployment.
10. Production requires explicit human authorization recorded according to `GOVERNANCE.md`.
11. Rollback is known before production deployment.
12. Environment-local runtime data are not promoted as if they were source artifacts.

## 4. Environment roles

### DEV

Purpose:

- implementation;
- debugging;
- automated tests;
- first technical verification.

Exit condition: stable enough to freeze the exact identity that has the required current `REVIEW_PASS`.

### TEST

Purpose:

- independent functional/integration validation;
- exact candidate verification.

Requirements:

- exact frozen candidate;
- independent verdict;
- no unresolved blocker/major defect.

Any implementation change returns to DEV and creates a new candidate identity.

### PROD

Purpose:

- run the exact TEST-passed candidate after explicit authorization.

Default post-deploy validation is a focused smoke test, not a second development cycle.

## 5. Release gates

### G1 — Scope approved

Minimum:

- approved Requirement;
- acceptance criteria;
- approved Architecture Gate where required.

### G2 — DEV PASS + Candidate Freeze

Minimum:

- implementation complete;
- required tests green;
- current `REVIEW_PASS` for the exact candidate identity that will be frozen;
- DEV verification pass;
- exact immutable `CANDIDATE_ID` recorded.

If the implementation changed after review, G2 fails until the changed candidate is reviewed again.

### G3 — TEST PASS

Minimum:

- TEST validates exact frozen candidate;
- expected behavior validated;
- no unresolved blocking defect;
- verdict recorded against candidate identity.

### G4 — PROD GO

Minimum:

- TEST-passed candidate is the one being promoted;
- integration did not rewrite candidate identity, or an equivalent immutable artifact mapping is proven;
- current review/test evidence applies to that exact identity;
- previous production identity captured;
- rollback action/reference known;
- explicit owner/approver authorization for that candidate is durably recorded.

For destructive/non-reversible data changes, require backup and non-PROD restore proof before PROD.

### G5 — PROD PASS / Close

Minimum:

- production runs expected candidate;
- smoke passes;
- Release Record complete.

## 6. Candidate identity

Preferred:

`CANDIDATE_ID = immutable source commit SHA`

Alternative immutable artifact IDs are acceptable when source identity cannot be promoted directly.

Invariant:

`reviewed candidate = DEV frozen candidate = TEST candidate = PROD candidate`

for one final promotion cycle.

## 7. Multi-wave releases

Intermediate validation checkpoints are allowed.

Only the Final Release Candidate may continue to production. Any implementation mutation produces a new identity and requires all evidence whose validity depends on the prior identity to be repeated.

## 8. Rollback

Prepare rollback before production.

### Code

Capture:

- previous known-good production identity;
- redeploy/restore procedure.

### Configuration

Also capture:

- previous config reference;
- restore action.

### Database / schema / destructive data change

Prefer backward-compatible migrations.

For destructive or non-reversible change require:

- backup;
- checksum or equivalent integrity evidence;
- demonstrated restore in non-PROD;
- rollback/cutover procedure.

## 9. Production failure

```text
STOP
→ execute predefined rollback when applicable
→ verify restored production identity/health
→ preserve evidence
→ fix in DEV
→ create new candidate
→ Evidence / Review / DEV / TEST / PROD again
```

Do not patch production ad hoc.

Forward-fix authorization for cases where rollback is impossible is not defined in v1.1.1 and remains a deferred finding.

## 10. Hotfix

Urgency may reduce **test breadth**, but it may not remove the controls that preserve authority, evidence, identity, and rollback safety.

Minimum non-reducible hotfix controls:

1. explicitly approved hotfix Requirement/scope;
2. approved ATC, which may be concise but must identify scope, stop conditions and required evidence;
3. implementation in DEV or the project-designated emergency development path;
4. Evidence Bundle for the exact implementation candidate;
5. Independent Review of that exact candidate;
6. DEV verification and candidate freeze;
7. targeted TEST of the exact frozen candidate;
8. rollback/predefined recovery check;
9. explicit `PROD_GO <candidate-ref>`;
10. PROD smoke and Release Record.

Only the breadth of TEST may be reduced for urgency, and that reduction must be explicitly accepted by the authorized approver. Requirement approval, ATC approval, candidate-bound review, candidate identity, rollback/recovery preparation and PROD authorization are not optional.

## 11. Minimal Release Record

```text
Requirement / work item
ATC / implementation reference
Reviewed candidate identity
Independent Review reference
CANDIDATE_ID
DEV PASS evidence
TEST PASS evidence
Previous PROD identity
Rollback action/reference
PROD GO record
PROD deploy evidence
PROD smoke verdict
```

Add only fields materially relevant to the release.
