# AgentFlow Changelog

## 1.2.0 — Pre-orchestration audit hardening

Status: release-ready; Independent Review `REVIEW_PASS`.

Based on the independent audit `AF-AUDIT-2026-09-23-01`.

### Correctness controls carried forward from the superseded v1.1.1 candidate

- F-02 — explicit Requirement Approval token.
- F-03 — review verdict bound to exact candidate identity.
- F-05 — minimum non-reducible hotfix controls.
- F-08 — one normative end-to-end process definition.
- F-09 — instruction provenance / untrusted-content rule.
- F-10 — durable approval record.
- F-12 — framework/document versioning foundation.
- F-13 — canonical status vocabulary alignment.
- F-16 — ATC is the only executable contract; Executable Task deprecated.
- F-25 — translated usage guide made non-normative.
- F-27 — canonical kit manifest.

### Added / completed in v1.2.0

- F-01 — evidence classes `ATTESTED / ARTIFACT / REPRODUCIBLE`; mandatory checks require ARTIFACT or stronger.
- F-04 — Candidate Manifest required before freeze and PROD GO.
- F-06 — review independence levels; `IR1_FRESH_CONTEXT` Core minimum.
- F-11 — `APPROVE_AGENTFLOW_BOOTSTRAP` added to canonical token/config model.
- F-12 — Core/template version matrix completed.
- F-13 — Evidence Bundle no longer emits implementation-phase statuses.
- F-14 — static typed artifact IDs and mandatory parent links.
- F-15 — config/Adapter precedence and complete pre-orchestration schema.
- F-17 — cross-cycle remediation budget and mandatory escalation.
- F-20 — explicit bounded forward-fix authorization/reconciliation path.
- F-22 — production-data/non-PROD rule and phase-scoped privilege boundary.
- F-23 — bootstrap/Adapter revalidation triggers and gap owner/closure rules.
- F-24 — static canonical metric vocabulary and optional gate-response expectations.
- F-26 — explicit applicability preconditions for non-git/nontraditional delivery.
- F-18 near-term subset — executor provenance and procedural single-active-executor/handoff.
- Development Analysis canonical template added.

### Explicit architectural boundary after v1.2

Not implemented:

- F-07 machine-readable state and automatic gate enforcement;
- automated artifact graph/composition verification;
- F-18 lock manager/concurrency/orchestrator;
- F-19 post-release observation as a first-class lifecycle phase;
- automatically derived state-transition metrics;
- agent router/orchestration engine;
- enterprise Security/Operations/Compliance adapters.

These require separate architecture work.

## 1.1.1 — Superseded pre-release candidate

Never merged/released as an independent framework version.

Its remediation work was carried into v1.2.0.

## 1.1.0 — Independent kit baseline

Initial standalone AgentFlow Framework extraction, bootstrap procedure, Core documents, templates, audit structure, and context handoff.
