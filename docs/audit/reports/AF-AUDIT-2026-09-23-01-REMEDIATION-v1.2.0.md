# AgentFlow Audit Remediation Ledger — v1.2.0

Status: `IMPLEMENTED_PENDING_INDEPENDENT_REVIEW`  
Source audit: `AF-AUDIT-2026-09-23-01`  
Audited baseline: `v1.1.0`  
Remediation candidate: `v1.2.0`

This document does **not** modify or reinterpret the original audit report. It records remediation disposition against the v1.2.0 candidate.

## Disposition vocabulary

- `IMPLEMENTED_PENDING_REVIEW` — remediation is present in the candidate but not yet independently verified.
- `PARTIAL_PENDING_REVIEW` — the current-architecture portion is implemented; the architectural/automated portion remains open.
- `DEFERRED_ARCHITECTURE` — requires future framework architecture/executable-state/orchestration work.
- `DEFERRED_EXTENSION` — belongs in a separate enterprise/organization adapter or extension.

## Finding ledger

| Finding | Candidate disposition | v1.2.0 remediation | Remaining boundary |
|---|---|---|---|
| F-01 | IMPLEMENTED_PENDING_REVIEW | Evidence classes ATTESTED/ARTIFACT/REPRODUCIBLE; mandatory checks require ARTIFACT or stronger; review blocks ATTESTED-only proof | automated evidence verification not claimed |
| F-02 | IMPLEMENTED_PENDING_REVIEW | `APPROVE_REQUIREMENT` canonical token/config/template | none in current architecture |
| F-03 | IMPLEMENTED_PENDING_REVIEW | review bound to exact candidate; candidate mutation invalidates review | automatic enforcement deferred with F-07 |
| F-04 | IMPLEMENTED_PENDING_REVIEW | Candidate Manifest required before freeze/PROD GO | automated composition verification deferred |
| F-05 | IMPLEMENTED_PENDING_REVIEW | non-reducible hotfix control set | none in current architecture |
| F-06 | IMPLEMENTED_PENDING_REVIEW | IR0/IR1/IR2/IR3 model; IR1 Core minimum | automated identity enforcement deferred |
| F-07 | DEFERRED_ARCHITECTURE | none | machine-readable state + policy/gate enforcement |
| F-08 | IMPLEMENTED_PENDING_REVIEW | Governance is single normative end-to-end process definition | none |
| F-09 | IMPLEMENTED_PENDING_REVIEW | instruction provenance/untrusted-content rules + access boundary | none |
| F-10 | IMPLEMENTED_PENDING_REVIEW | durable approval record required in Adapter/config/bootstrap | none |
| F-11 | IMPLEMENTED_PENDING_REVIEW | `APPROVE_AGENTFLOW_BOOTSTRAP` canonical token/config | none |
| F-12 | IMPLEMENTED_PENDING_REVIEW | independent Core/template version metadata + changelog/compatibility/version matrix | none |
| F-13 | IMPLEMENTED_PENDING_REVIEW | ADR canonical statuses; Evidence artifact emits EVIDENCE statuses only | none |
| F-14 | PARTIAL_PENDING_REVIEW | static typed artifact IDs + mandatory parent links + release trace chain | automated artifact graph/dependency verification deferred |
| F-15 | IMPLEMENTED_PENDING_REVIEW | config authoritative for machine values; Adapter authoritative for rationale; overlap must match; expanded schema | generic validator deferred with F-07 |
| F-16 | IMPLEMENTED_PENDING_REVIEW | ATC only executable contract; Executable Task deprecated compatibility view | none |
| F-17 | IMPLEMENTED_PENDING_REVIEW | default cross-cycle remediation budget + mandatory escalation | automatic counting/enforcement deferred |
| F-18 | PARTIAL_PENDING_REVIEW | executor identity/provenance + procedural single-active-executor and recorded handoff | lock manager, concurrency, duplicate detection, abandonment recovery, orchestrator deferred |
| F-19 | DEFERRED_ARCHITECTURE | no new lifecycle phase added | post-release observation phase + Operations/Incident adapter |
| F-20 | IMPLEMENTED_PENDING_REVIEW | explicit `APPROVE_FORWARD_FIX` path + evidence/reconciliation rules | automated incident orchestration not claimed |
| F-21 | DEFERRED_EXTENSION | none in Core | Security Adapter / secure-SDLC controls |
| F-22 | IMPLEMENTED_PENDING_REVIEW | production-data non-PROD approval/minimisation rule + phase-scoped credential/environment boundaries | enterprise privacy adapter may strengthen |
| F-23 | IMPLEMENTED_PENDING_REVIEW | last validated, revalidation triggers, gap owner + closure condition | automated expiry/revalidation engine not claimed |
| F-24 | IMPLEMENTED_PENDING_REVIEW | canonical static metrics vocabulary + optional gate response expectations | automatic metrics from state transitions deferred |
| F-25 | IMPLEMENTED_PENDING_REVIEW | Romanian usage guide reduced to non-normative use/adoption guidance | none |
| F-26 | IMPLEMENTED_PENDING_REVIEW | explicit applicability preconditions + non-git immutable-identity guidance + bootstrap fail-closed | none |
| F-27 | IMPLEMENTED_PENDING_REVIEW | KIT-MANIFEST canonical inventory; version matrix introduced | generated inventory tooling not required |

## Architectural boundary after v1.2.0

The following must not be implemented as incremental documentation patches:

1. machine-readable workflow state and transition engine;
2. generic policy/gate validator;
3. automated artifact graph/composition verification;
4. multi-agent locking/concurrency/scheduling;
5. orchestrator/router and automated abandonment recovery;
6. post-release observation as a new Core lifecycle phase;
7. automatic state-derived metrics.

Those require Architecture decisions for the next major framework generation.

## Verification status

This ledger is **not** evidence that the findings are closed.

Closure requires Independent Review of the exact v1.2.0 candidate and, for stronger assurance, a follow-up external audit against the released framework and completed delivery instances.
