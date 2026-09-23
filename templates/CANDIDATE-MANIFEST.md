# Candidate Manifest

Template status: `CANONICAL`  
Template version: `1.0.0`  
Framework compatibility: `1.2.x`

## Identity

- Candidate Manifest ID: `CM-<candidate-ref>`
- Exact candidate ID:
- Candidate type: `source commit | artifact hash | snapshot | package | other`
- Base / previous identity:
- Created by:
- Timestamp:

## Included work

Each included item must be traceable to approved/evidenced/reviewed work.

| Requirement | DA | ATC | Evidence Bundle | Independent Review | Reviewed candidate ID | Verdict |
|---|---|---|---|---|---|---|
| | | | | | | |

All included review candidate IDs must equal the manifest's exact candidate ID or have a documented composition mapping proving inclusion without identity drift.

## Relevant architecture decisions

- 

## Candidate composition reference

- Compare/change-set/artifact composition reference:
- Integration/build reference:
- Notes:

v1.2 records composition statically. Automated dependency/composition verification is not claimed.

## Known exclusions / limitations

- 

## Manifest completeness

- [ ] every included change is represented by an ATC/work item
- [ ] every included ATC has required approval
- [ ] every included ATC has Evidence Bundle
- [ ] every included ATC has applicable REVIEW_PASS
- [ ] review candidate binding matches this candidate or an explicit immutable composition mapping
- [ ] no unknown/unattributed change is included

## Freeze gate

- DEV verification reference:
- Manifest complete: YES / NO
- Candidate may be frozen: YES / NO

If NO, candidate cannot proceed to TEST or PROD.
