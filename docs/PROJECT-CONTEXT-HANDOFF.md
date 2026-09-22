# AgentFlow Framework — Project Context Handoff

Status: `CURRENT CONTEXT`
Last updated: `2026-09-23`
Framework baseline: `Independent Kit v1.1.0`

## 1. Purpose

This document exists so a new chat or agent can continue work on AgentFlow without access to the conversations in which the framework was created.

It is context, not a substitute for canonical Core documents.

## 2. Current repository purpose

`AgentFlow_Framework` is the independent home of AgentFlow.

The framework was extracted from delivery practices first developed and exercised in another software project, then generalized so the Core is not coupled to that project, GitHub, Cloudflare, Nile/PostgreSQL, Claude, ChatGPT, or any other specific platform.

The original application project should be treated as a reference implementation / proving ground, not as the source of truth for future AgentFlow Core development.

## 3. Current framework state

Current kit version: `1.1.0`.

Core currently defines:

- requirement and approval boundaries;
- architecture delta/gate;
- Development Analysis;
- Agent Task Contracts;
- explicit scoped execution approval;
- retry limits and stop conditions;
- Evidence Bundle;
- Independent Review;
- DEV → frozen candidate → TEST → PROD lifecycle;
- rollback-before-PROD;
- source-of-truth hierarchy;
- progressive context loading;
- greenfield/existing-project bootstrap;
- Project Adapter separation.

## 4. Key design decisions already made

### Core vs adapters

Core remains tool-neutral.

Project-specific concerns belong in Project Adapter/configuration.

Organization-scale security/compliance/change-management controls should become Organization/Security adapters rather than automatically expanding Core.

### Existing-project adoption

Do not perform big-bang process conversion.

Default transition:

```text
new work -> AGENTFLOW
materially started work -> LEGACY-ADAPTED
```

### Bootstrap

Bootstrap is read-only by default and generates:

- Project Adapter;
- machine-readable configuration;
- Bootstrap Report;
- adoption verdict.

### Execution authority

Development Analysis does not authorize implementation.

An ATC becomes executable only after explicit approval scoped to that ATC.

### Release identity

One final immutable candidate must be the identity verified through DEV, TEST and PROD, or the project must provide an equivalent immutable artifact mapping.

## 5. Original problem / JTBD

The strongest current product insight is that AgentFlow exists primarily because work distributed across chats becomes difficult to resume safely.

The framework's underlying job-to-be-done is:

> preserve project continuity, decision authority and traceability across independent AI sessions.

See `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.

## 6. Current maturity assessment

Current judgement:

- process/governance maturity: high;
- release lifecycle maturity: high;
- agent execution model: medium-high;
- machine enforcement: medium-low;
- multi-agent orchestration: medium-low.

AgentFlow is usable as a real process framework for solo/small-team projects, but is not yet an autonomous delivery platform.

See `docs/reference/MATURITY-ASSESSMENT-RO.md`.

## 7. Important gaps / future candidates

Highest-value evolution candidates currently identified:

1. formal continuation/resume contract;
2. machine-readable state machine;
3. artifact graph / traceability model;
4. automated gate validation / policy enforcement;
5. framework metrics;
6. multi-agent locking, provenance and recovery;
7. Security SDLC adapter;
8. Operations / Incident adapter.

Do not assume these are approved roadmap commitments. They are current candidates.

## 8. Market position — current working view

Relevant neighboring tools include:

- GitHub Spec Kit;
- BMad Method;
- Kiro;
- GitLab Duo Agent Platform.

Spec Kit and BMad are the closest free/open-source references currently identified.

The current differentiation hypothesis is not "specification before coding" or "multiple AI agents". It is the combination of:

- conversation-independent project state;
- explicit decision authority;
- bounded execution contracts;
- stop/fail-closed behavior;
- evidence/review separation;
- immutable release promotion.

See `docs/research/MARKET-LANDSCAPE.md`.

## 9. Naming

`AgentFlow` should currently be treated as a working/project name.

No trademark or naming clearance has been performed in this repository.

Do not make legal or branding claims without a separate naming/trademark check.

## 10. External audit

A structured external-audit template exists under:

`docs/audit/EXTERNAL-AUDIT-TEMPLATE.md`

The audit is designed to distinguish:

- documented;
- implemented;
- enforced;
- verified;
- missing.

An external audit has not yet been recorded in this repository.

## 11. Next sensible analysis

Before building an orchestration engine from scratch, compare AgentFlow against current capabilities of Spec Kit, BMad and relevant platform governance tooling.

Focus on:

- what AgentFlow should reuse or integrate;
- what would duplicate existing free tooling;
- what belongs uniquely in AgentFlow Core;
- whether AgentFlow can operate as a governance/control layer over an existing workflow engine.

## 12. Cold-start instruction for a new agent

Start with:

1. `README.md`;
2. this file;
3. `docs/design/ORIGIN-AND-DESIGN-INTENT.md`;
4. only the Core document relevant to the current question;
5. current Issue/task if one exists.

Do not reconstruct state from external chat history unless project artifacts are insufficient.
