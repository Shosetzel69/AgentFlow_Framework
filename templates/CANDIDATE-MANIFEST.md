# Candidate Manifest

Template status: `CANONICAL`  
Template version: `1.1.0`  
Framework compatibility: `1.3.x`

## Identity
- Candidate Manifest ID: `CM-<candidate-ref>`
- Exact candidate ID:
- Candidate type: `source commit | artifact hash | snapshot | package | other`
- Base / previous identity:
- Created by:
- Timestamp:

## Included work
| Requirement | DA | ATC | Evidence Bundle | Independent Review | Reviewed candidate ID | Verdict |
|---|---|---|---|---|---|---|
| | | | | | | |

## Relevant architecture decisions
-

## Candidate composition proof
When included work was reviewed at a different immutable component/source identity, provide an independently verifiable mapping proving unchanged inclusion.

Accepted examples include:
- identical tree/content hash;
- demonstrably identical integration tree;
- deterministic artifact/package digest mapping;
- equivalent reproducible build/provenance mapping.

- Proof/reference:
- Evidence class: `ARTIFACT | REPRODUCIBLE | BOTH`
- Independently verifiable: YES / NO

If composition equivalence cannot be independently verified, produce fresh evidence/review for this candidate.

## Known exclusions / limitations
-

## Manifest completeness
- [ ] every change maps to approved work
- [ ] each ATC has required approval
- [ ] each ATC has candidate-bound Evidence Bundle
- [ ] each ATC has applicable REVIEW_PASS
- [ ] candidate/composition identity is independently verifiable
- [ ] no unknown/unattributed change is included

## Freeze gate
- DEV verification reference:
- Manifest complete: YES / NO
- Candidate may be frozen: YES / NO

If NO, candidate cannot proceed to TEST or PROD.
