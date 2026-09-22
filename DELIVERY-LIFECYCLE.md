# AgentFlow Delivery Lifecycle — DEV → TEST → PROD

Status: `REFERENCE CORE`
Version: `1.0.0`

## 1. Goal

The release process must answer at any time:

1. What change is being released?
2. What exact artifact or source identity was tested?
3. What exact identity is running in production?
4. How do we return to the previous known-good state?

## 2. Canonical flow

```text
Approved implementation
→ DEV verification
→ freeze CANDIDATE_ID
→ TEST exact same candidate
→ TEST PASS
→ integrate/publish without identity rewrite
→ rollback preflight
→ explicit PROD GO
→ PROD exact same candidate
→ smoke PASS
→ close
```

Failure flow:

```text
TEST FAIL
→ DEV remediation
→ new candidate identity
→ DEV verification
→ TEST again
```

## 3. Non-negotiable rules

1. The protected default branch is not a development or debugging environment.
2. Source changes use the project-approved branch/review mechanism.
3. DEV is the normal implementation/debugging environment.
4. TEST validates the exact frozen candidate.
5. Fixes are not made directly in TEST.
6. Any source change after candidate freeze creates a new candidate and invalidates the previous TEST result.
7. Merge/integration does not itself authorize production deployment.
8. Production requires explicit human authorization.
9. Rollback is known before production deployment.
10. Environment-local runtime data are not promoted as if they were source artifacts.

## 4. Environment roles

### DEV

Purpose:

- implementation;
- debugging;
- automated tests;
- first technical verification.

Exit condition: stable enough to freeze one immutable candidate identity.

### TEST

Purpose:

- independent functional/integration validation;
- exact candidate verification.

Requirements:

- exact frozen candidate;
- independent verdict;
- no unresolved blocker/major defect.

Any source fix returns to DEV.

### PROD

Purpose:

- run the exact TEST-passed candidate after explicit authorization.

Default post-deploy validation is a focused smoke test, not a second development cycle.

## 5. Release gates

### G1 — Scope approved

Minimum:

- approved requirement;
- acceptance criteria;
- approved Architecture Gate where required.

### G2 — DEV PASS + Candidate Freeze

Minimum:

- implementation complete;
- required tests green;
- DEV verification pass;
- exact immutable `CANDIDATE_ID` recorded.

### G3 — TEST PASS

Minimum:

- TEST validates exact candidate;
- expected behavior validated;
- no unresolved blocking defect;
- verdict recorded against candidate identity.

### G4 — PROD GO

Minimum:

- TEST-passed candidate is the one being promoted;
- integration did not rewrite candidate identity, or an equivalent immutable artifact mapping is proven;
- previous production identity captured;
- rollback action/reference known;
- explicit owner/approver authorization.

For destructive/non-reversible data changes, require backup and non-PROD restore proof before PROD.

### G5 — PROD PASS / Close

Minimum:

- production runs expected candidate;
- smoke passes;
- Release Record complete.

## 6. Candidate identity

Preferred:

```text
CANDIDATE_ID = immutable source commit SHA
```

Alternative immutable artifact IDs are acceptable when source identity cannot be promoted directly.

Invariant:

```text
DEV candidate = TEST candidate = PROD candidate
```

for one final promotion cycle.

## 7. Multi-wave releases

Intermediate validation checkpoints are allowed.

```text
wave
→ DEV
→ freeze CHECKPOINT_ID
→ TEST
→ checkpoint verdict
→ STOP before PROD
→ next wave
```

Only the Final Release Candidate may continue to production.

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
→ DEV → TEST → PROD again
```

Do not patch production ad hoc.

## 10. Hotfix

Urgency may reduce test breadth but not the core controls:

```text
Hotfix scope
→ DEV
→ freeze candidate
→ targeted TEST
→ rollback check
→ explicit PROD GO
→ PROD
```

Any reduced test scope must be explicitly accepted by the authorized approver.

## 11. Minimal Release Record

```text
Requirement / work item
Implementation reference
CANDIDATE_ID
DEV PASS evidence
TEST PASS evidence
Previous PROD identity
Rollback action/reference
PROD GO
PROD deploy evidence
PROD smoke verdict
```

Add only fields materially relevant to the release.
