# AgentFlow Delivery Framework — Independent Kit

Version: `1.2.0`  
Status: `REFERENCE CORE`

## Purpose

AgentFlow is a lightweight software-delivery framework for projects where AI agents participate in requirements, architecture, implementation, review, testing, documentation, and release work.

Its purpose is to preserve:

- **continuity** across chats, agents, and sessions;
- **authority** over material decisions and execution;
- **traceability** from Requirement to production evidence.

The framework is tool-neutral. Source-control platforms, issue trackers, cloud providers, databases, AI products, and CI/CD systems are Project Adapter concerns rather than Core dependencies.

## Start here

For framework adoption:

1. `GOVERNANCE.md` — single normative end-to-end process definition;
2. `AGENTFLOW.md` — Development Analysis, execution, evidence, review;
3. `DELIVERY-LIFECYCLE.md` — release promotion/recovery;
4. `ARTIFACT-TRACEABILITY.md` — typed IDs and parent links;
5. `FRAMEWORK-CONFIG.md` and `BOOTSTRAP-PROCEDURE.md`;
6. generate a Project Adapter/config using the templates.

For framework development or a fresh AI session:

1. read `docs/PROJECT-CONTEXT-HANDOFF.md`;
2. inspect the current framework Issue/PR;
3. load only the relevant Core document.

Canonical shipped-file inventory: `KIT-MANIFEST.md`.

## Core principles

1. Decide before coding.
2. Contract before execution.
3. Stop on material uncertainty.
4. Prove what was executed.
5. Review independently.
6. Promote one immutable candidate.

## v1.2 focus

v1.2 is the **pre-orchestration hardening release**.

It adds:

- evidence classes and proof-strength rules;
- graded Independent Review independence;
- Candidate Manifest;
- static typed artifact identity and parent links;
- durable bootstrap/requirement/task/release approvals;
- cross-cycle remediation budget;
- executor provenance and procedural single-active-executor/handoff;
- forward-fix exception control;
- phase-scoped access and production-data handling;
- bootstrap revalidation;
- static metrics vocabulary;
- complete config/Adapter precedence.

It intentionally does **not** add:

- machine-readable state engine;
- automatic policy/gate enforcement;
- automated artifact graph;
- lock manager/concurrency scheduler;
- agent orchestrator/router;
- post-release operations lifecycle;
- enterprise Security/Operations/Compliance adapters.

Those require later architecture work.

## Applicability

Before adoption a project must establish:

- durable work/change record;
- durable approval record;
- immutable or equivalently verifiable candidate identity;
- change-review mechanism;
- inspectable delivery state/tooling.

Git is not required. Low-code/SaaS/binary delivery may use immutable snapshots, exports, package hashes, or equivalent identities.

If an equivalent control cannot be established, bootstrap returns `BLOCKED`.

## Minimum adoption

For a small project, adopt at least:

- `GOVERNANCE.md`;
- `AGENTFLOW.md`;
- `DELIVERY-LIFECYCLE.md`;
- `AI-EXECUTION-RULES.md`;
- `ARTIFACT-TRACEABILITY.md`;
- `templates/REQUIREMENT.md`;
- `templates/DEVELOPMENT-ANALYSIS.md`;
- `templates/AGENT-TASK-CONTRACT.md`;
- `templates/EVIDENCE-BUNDLE.md`;
- `templates/INDEPENDENT-REVIEW.md`;
- `templates/CANDIDATE-MANIFEST.md`;
- project-specific `PROJECT-ADAPTER.md` and `agentflow.config.yaml`.

## Framework Core vs Project Adapter

Core defines generic safety/authority/traceability rules.

Project Adapter/config define:

- platforms/toolchain;
- record locations;
- artifact-ID mapping;
- environment/access boundaries;
- candidate identity mechanism;
- approval token mapping;
- review independence level;
- project architecture triggers;
- evidence/recovery policy;
- revalidation and metrics expectations.

## Versioning / upgrade

- current kit version: `VERSION`;
- release semantics: `CHANGELOG.md`;
- upgrade mapping: `COMPATIBILITY.md`;
- shipped artifact versions: `docs/reference/CORE-VERSION-MATRIX.md`;
- canonical inventory: `KIT-MANIFEST.md`.

A framework release never modifies a consuming application automatically.

## Design intent

AgentFlow originated from a practical continuity problem: software work spread across multiple AI chats becomes difficult to resume safely.

> No information required for controlled continuation of the project should exist exclusively in a conversation.

See `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.

## License

No project license has been selected yet. Do not assume reuse/distribution terms until a license is explicitly added.
