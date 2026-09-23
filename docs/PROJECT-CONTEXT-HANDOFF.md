# AgentFlow Framework — Project Context Handoff

Status: `CURRENT CONTEXT`  
Last updated: `2026-09-23`  
Framework candidate: `v1.2.0 pre-orchestration audit hardening`

## 1. Purpose

This document allows a new chat/agent to continue AgentFlow Framework work without access to the conversations that created it.

It is context, not a substitute for canonical Core.

## 2. Repository purpose

`AgentFlow_Framework` is the independent home of AgentFlow.

Consuming applications are proving grounds / consumers. Framework changes never propagate automatically to them.

## 3. Current work

Active work item: Issue #8 — v1.2.0 pre-orchestration audit hardening.

v1.2.0 supersedes the narrower unmerged v1.1.1 candidate from Issue #5 / PR #6.

The independent audit of the v1.1.0 baseline remains at:

`docs/audit/reports/AF-AUDIT-2026-09-23-01.md`

## 4. Current canonical sources

- `GOVERNANCE.md` — single normative end-to-end process, phases/statuses, approvals.
- `AGENTFLOW.md` — Development Analysis, execution, evidence, review.
- `DELIVERY-LIFECYCLE.md` — candidate/release/recovery controls.
- `AI-EXECUTION-RULES.md` — agent instruction/access/evidence rules.
- `ARTIFACT-TRACEABILITY.md` — typed artifact IDs and parent links.
- `FRAMEWORK-CONFIG.md` — Project Adapter/config schema and precedence.
- `DOCUMENTATION-POLICY.md` — documentation/context/versioning.
- `METRICS.md` — static metric vocabulary.
- `KIT-MANIFEST.md` — canonical shipped-file inventory.
- `docs/reference/CORE-VERSION-MATRIX.md` — exact shipped document/template versions.

## 5. v1.2 objective

v1.2 completes all audit hardening that can be implemented without redesigning AgentFlow into an executable orchestration platform.

It includes:

- explicit/durable approvals including bootstrap;
- evidence classes;
- candidate-bound review;
- review independence levels;
- Candidate Manifest;
- static artifact IDs/links;
- config/Adapter precedence;
- cross-cycle remediation budget;
- executor provenance + single-active-executor/handoff rule;
- forward-fix exception;
- phase access boundaries;
- production-data/non-PROD control;
- bootstrap revalidation;
- metrics vocabulary;
- applicability preconditions.

## 6. Explicit architectural boundary after v1.2

Do not silently implement the following without a new Architecture decision:

- machine-readable work-item state engine;
- automated policy/gate enforcement;
- automated artifact graph/dependency verification;
- lock manager/concurrency scheduler;
- duplicate-execution detection engine;
- agent router/orchestrator;
- automatic abandonment recovery;
- post-release observation as a new first-class lifecycle phase;
- automated state-transition metrics;
- enterprise Security/Operations/Compliance adapters if they materially change Core.

These are future architecture items, not unfinished v1.2 documentation.

## 7. Original problem / JTBD

AgentFlow exists because software delivery spread across AI chats/sessions becomes difficult to resume safely.

> Preserve project continuity, decision authority and traceability across independent AI sessions.

See `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.

## 8. Cold-start instruction

Start with:

1. this file;
2. current framework Issue/PR;
3. `README.md`;
4. only the relevant canonical Core document;
5. audit/remediation material only when the task concerns a finding.

Do not reconstruct current state from external chat history unless project artifacts are insufficient.
