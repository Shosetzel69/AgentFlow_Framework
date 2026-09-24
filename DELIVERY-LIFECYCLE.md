# AgentFlow Delivery Lifecycle — DEV → TEST → PROD

Status: `REFERENCE CORE`  
Document version: `1.3.0`  
Framework compatibility: `1.3.x`

## 1. Goal

The release process must answer at any time:

1. What change is being released?
2. What exact artifact or source identity was reviewed and tested?
3. Which approved work items are contained in that candidate?
4. What exact identity is running in production?
5. How do we recover if production fails?

The normative end-to-end AgentFlow process is defined in `GOVERNANCE.md`. This document governs release promotion.

## 2. Release flow

```text
reviewed implementation candidate
→ DEV verification
→ build/complete Candidate Manifest
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
→ Candidate Manifest
→ TEST again
```

## 3. Non-negotiable rules

1. The protected/default integration target is not a development or debugging environment.
2. Changes use the project-approved change/review mechanism.
3. DEV is the normal implementation/debugging environment.
4. Independent Review verdicts are bound to one exact candidate identity.
5. Candidate mutation after `REVIEW_PASS` invalidates that review for promotion and requires a new review of the changed candidate.
6. A complete Candidate Manifest is required before candidate freeze.
7. TEST validates the exact frozen candidate.
8. Fixes are not made directly in TEST.
9. Any source/content change after candidate freeze creates a new candidate and invalidates the previous TEST result.
10. Merge/integration does not itself authorize production deployment.
11. Production requires explicit human authorization recorded according to `GOVERNANCE.md`.
12. PROD_GO is valid only for the exact Candidate Manifest/candidate identity approved.
13. Rollback is known before production deployment unless the explicitly controlled forward-fix exception is invoked.
14. Environment-local runtime data are not promoted as if they were source artifacts.
15. Production data is not copied into non-production except under the explicit privacy/data-use control in `AI-EXECUTION-RULES.md`.

## 4. Environment roles

### DEV

Purpose:

- implementation;
- debugging;
- automated tests;
- first technical verification.

Exit condition: stable enough to complete a Candidate Manifest and freeze the exact identity that has the required current `REVIEW_PASS`.

### TEST

Purpose:

- independent functional/integration validation;
- exact candidate verification.

Requirements:

- exact frozen candidate;
- Candidate Manifest;
- independent verdict;
- no unresolved blocker/major defect.

Any implementation change returns to DEV and creates a new candidate identity.

### PROD

Purpose:

- run the exact TEST-passed candidate after explicit authorization.

Default post-deploy validation is a focused smoke test, not a second development cycle.

Post-release observation as a new formal lifecycle phase is intentionally not introduced in v1.2.

## 5. Release gates

### G1 — Scope approved

Minimum:

- approved Requirement;
- acceptance criteria;
- approved Architecture Gate where required.

### G2 — DEV PASS + Candidate Manifest + Freeze

Minimum:

- implementation complete;
- mandatory checks satisfy required evidence class;
- current `REVIEW_PASS` for the exact candidate identity that will be frozen;
- DEV verification pass;
- Candidate Manifest complete;
- exact immutable `CANDIDATE_ID` recorded.

If the implementation changed after review, G2 fails until the changed candidate is evidenced and reviewed again.

### G3 — TEST PASS

Minimum:

- TEST validates exact frozen candidate;
- Candidate Manifest identity matches the tested candidate;
- expected behavior validated;
- no unresolved blocking defect;
- verdict recorded against candidate identity.

### G4 — PROD GO

Before PROD_GO, classify every affected persistent target environment as `ALREADY_COMPLIANT`, `TRUSTED_BOOTSTRAP`, `APPROVED_TRANSITION_READY`, or `BLOCKED`. Any unresolved `BLOCKED` target yields `RELEASE_BLOCKED`. This is a release-readiness condition, not a new human approval gate.

Minimum:

- TEST-passed candidate is the one being promoted;
- Candidate Manifest is complete and current;
- every included ATC/work item in the manifest has the required approval/evidence/review references;
- integration did not rewrite candidate identity, or composition/equivalence is proven by independently verifiable ARTIFACT or REPRODUCIBLE evidence;
- current review/test evidence applies to that exact identity;
- previous production identity captured;
- rollback action/reference known, or forward-fix exception conditions explicitly satisfied;
- explicit owner/approver authorization for that candidate is durably recorded.

For destructive/non-reversible data changes, require backup and non-PROD restore proof before PROD where rollback is expected to be feasible.

### G5 — PROD PASS / Close

Minimum:

- production runs expected candidate;
- smoke passes;
- Release Record complete;
- production state remains traceable to the Candidate Manifest.

## 6. Candidate identity

Preferred:

`CANDIDATE_ID = immutable source commit SHA`

Alternative immutable artifact IDs are acceptable when source identity cannot be promoted directly.

Invariant:

`reviewed candidate = DEV frozen candidate = TEST candidate = PROD candidate`

for one final promotion cycle.

For platforms without promotable source identity, bootstrap must establish an equivalent immutable artifact/snapshot/hash identity before adoption may be `READY_TO_ADOPT`.

## 7. Candidate Manifest

Every frozen candidate has one Candidate Manifest using `templates/CANDIDATE-MANIFEST.md`.

The manifest records:

- manifest ID;
- exact candidate ID;
- base/previous identity when relevant;
- every included Requirement/ATC;
- relevant ADR/DA links;
- Evidence Bundle reference per included ATC;
- Independent Review reference and reviewed candidate ID per included ATC;
- known exclusions/limitations;
- manifest author and timestamp.

The manifest is a static traceability control. Automated dependency/composition verification remains deferred. If equivalence to a previously reviewed identity cannot be independently verified, fresh evidence/review is required for the candidate proceeding.

Any candidate mutation invalidates the prior manifest for promotion.

## 8. Multi-wave releases

Intermediate validation checkpoints are allowed.

Only the Final Release Candidate may continue to production. Any implementation mutation produces a new identity and requires all evidence whose validity depends on the prior identity to be repeated.

## 9. Rollback

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

For destructive or non-reversible change require, where technically feasible:

- backup;
- integrity evidence;
- demonstrated restore in non-PROD;
- rollback/cutover procedure.

## 10. Production failure

Normal path:

```text
STOP
→ execute predefined rollback when applicable
→ verify restored production identity/health
→ preserve evidence
→ fix in DEV
→ create new candidate
→ Evidence / Review / DEV / Candidate Manifest / TEST / PROD again
```

Do not patch production ad hoc.

## 11. Forward-fix exception

Forward-fix is an emergency exception for cases where rollback is **demonstrably not feasible** within the required recovery window.

Before forward-fix begins, record:

- incident/release reference;
- current production identity/state;
- why rollback is not feasible;
- bounded forward-fix objective/scope;
- minimum validation/evidence that can be performed safely;
- named owner/approver;
- recovery/reconciliation plan.

Required authorization:

`APPROVE_FORWARD_FIX <ref>`

Rules:

1. use an emergency candidate identity whenever the platform permits it;
2. preserve all available evidence;
3. perform independent review/targeted validation to the maximum feasible level before mutation;
4. if direct production mutation is unavoidable, record every change;
5. create/reconcile an immutable source/artifact candidate representing the resulting production state immediately after stabilization;
6. perform mandatory post-incident reconciliation so repository/artifact identity and production state match;
7. do not close the release while production cannot be traced to a durable candidate identity.

Forward-fix does not authorize unrelated changes.

## 12. Hotfix

Urgency may reduce **test breadth**, but it may not remove the controls that preserve authority, evidence, identity, and recovery safety.

Minimum non-reducible hotfix controls:

1. explicitly approved hotfix Requirement/scope;
2. approved ATC;
3. implementation in DEV or project-designated emergency development path;
4. Evidence Bundle for exact implementation candidate;
5. Independent Review of that exact candidate;
6. DEV verification;
7. Candidate Manifest and freeze;
8. targeted TEST of the exact frozen candidate;
9. rollback/recovery preflight;
10. explicit `PROD_GO <candidate-ref>`;
11. PROD smoke and Release Record.

Only the breadth of TEST may be reduced for urgency, and that reduction must be explicitly accepted by the authorized approver.

## 13. Minimal Release Record

```text
Release ID
Requirement(s)
ATC(s)
Candidate Manifest ID
Reviewed candidate identity
Independent Review reference(s)
CANDIDATE_ID
DEV PASS evidence
TEST PASS evidence
Previous PROD identity
Rollback action/reference or Forward-Fix authorization
PROD GO record
PROD deploy evidence
PROD smoke verdict
```

Add only fields materially relevant to the release, but do not omit required traceability links.
