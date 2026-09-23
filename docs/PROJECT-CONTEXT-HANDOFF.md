# AgentFlow Framework — Project Context Handoff

Status: `CURRENT CONTEXT`  
Last updated: `2026-09-23`  
Framework baseline: `v1.1.1 audit-remediation candidate`

## 1. Purpose

This document exists so a new chat or agent can continue work on AgentFlow without access to the conversations in which the framework was created.

It is context, not a substitute for canonical Core documents.

## 2. Current repository purpose

`AgentFlow_Framework` is the independent home of AgentFlow.

The framework was extracted from delivery practices first developed and exercised in another software project, then generalized so Core is not coupled to that project or to a specific source-control platform, cloud, database, or AI product.

Consuming applications are reference implementations / proving grounds. They are not automatically modified when this repository changes.

## 3. Current framework state

Current release line: `1.1.x`.

Active remediation work: Issue #5, target `v1.1.1`.

The independent audit `AF-AUDIT-2026-09-23-01` is stored under `docs/audit/reports/`.

v1.1.1 addresses the audit's patch-level correctness/consistency findings:

- explicit Requirement Approval token;
- durable approval records;
- review-to-candidate binding and invalidation;
- minimum hotfix controls;
- one normative process definition;
- AI instruction provenance;
- version/status vocabulary consistency;
- ATC vs Executable Task ambiguity;
- usage-guide and manifest source-of-truth drift.

Machine enforcement, artifact graph, evidence classes, multi-agent coordination, operations adapters, and metrics remain deferred.

## 4. Canonical sources

- `GOVERNANCE.md` — single normative end-to-end process, phases/statuses, approvals;
- `AGENTFLOW.md` — analysis/execution/evidence/review operational contract;
- `DELIVERY-LIFECYCLE.md` — release promotion;
- `AI-EXECUTION-RULES.md` — agent behavior and instruction provenance;
- `DOCUMENTATION-POLICY.md` — context/documentation;
- `KIT-MANIFEST.md` — canonical kit inventory.

Convenience/reference documents must not override these sources.

## 5. Original problem / JTBD

AgentFlow exists primarily because work distributed across chats becomes difficult to resume safely.

Underlying job-to-be-done:

> preserve project continuity, decision authority and traceability across independent AI sessions.

See `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.

## 6. Key design boundaries

### Core vs adapters

Core remains tool-neutral.

Project-specific concerns belong in Project Adapter/configuration.

Organization-scale security/compliance/change-management controls should become adapters rather than automatically expanding Core.

### Existing-project adoption

Do not perform big-bang conversion.

### Execution authority

Development Analysis does not authorize implementation.

An ATC becomes executable only after the required scoped approval is durably recorded.

### Review identity

Review verdicts apply to one exact candidate identity. Implementation mutation invalidates the old verdict for promotion.

### Release identity

One immutable candidate must be the identity carried through the final review/DEV/TEST/PROD promotion cycle, or the project must prove an equivalent immutable artifact mapping.

## 7. Current maturity / deferred candidates

Important future candidates:

1. evidence integrity classes;
2. machine-readable state and gate validation;
3. canonical artifact IDs / artifact graph;
4. candidate composition manifest;
5. cross-cycle budget/escalation;
6. metrics;
7. multi-agent identity, locking, provenance and recovery;
8. Security / Operations / Compliance adapters.

These are candidates, not automatically approved roadmap commitments.

## 8. Market position

Relevant neighboring tools include GitHub Spec Kit, BMad Method, Kiro, and GitLab Duo Agent Platform.

Current differentiation hypothesis:

- conversation-independent project state;
- explicit decision authority;
- bounded execution contracts;
- fail-closed behavior;
- evidence/review separation;
- immutable release promotion.

See `docs/research/MARKET-LANDSCAPE.md`.

## 9. Naming

`AgentFlow` remains a working/project name. No trademark clearance has been performed.

## 10. Cold-start instruction for a new agent

Start with:

1. `README.md`;
2. this file;
3. current Issue/task;
4. only the relevant canonical Core document;
5. `docs/design/ORIGIN-AND-DESIGN-INTENT.md` when design intent is material.

Do not reconstruct current state from external chat history unless project artifacts are insufficient.
