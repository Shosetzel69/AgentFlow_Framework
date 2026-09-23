# AgentFlow Delivery Framework — Independent Kit

Version: `1.1.1`  
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

1. read `GOVERNANCE.md` — **single normative end-to-end process definition**;
2. read `AGENTFLOW.md` — analysis/execution/evidence/review operational rules;
3. read `DELIVERY-LIFECYCLE.md` — release promotion rules;
4. use `BOOTSTRAP-PROCEDURE.md`;
5. generate a Project Adapter from `templates/PROJECT-ADAPTER.md`.

For framework development or a fresh AI session:

1. read `docs/PROJECT-CONTEXT-HANDOFF.md`;
2. read `docs/design/ORIGIN-AND-DESIGN-INTENT.md`;
3. load only the Core document relevant to the current task.

The **canonical kit inventory** is `KIT-MANIFEST.md`. Do not treat README examples or translated guidance as an alternative inventory or process definition.

## Core principles

1. **Decide before coding.**
2. **Contract before execution.**
3. **Stop on material uncertainty.**
4. **Prove what was executed.**
5. **Review independently.**
6. **Promote one immutable candidate.**

## Bootstrap a new project

Start with `BOOTSTRAP-PROCEDURE.md`.

Bootstrap inspects the target project in read-only mode, builds the source-of-truth and gap maps, and proposes:

- `PROJECT-ADAPTER.md`;
- `agentflow.config.yaml`;
- `BOOTSTRAP-REPORT.md`.

Activation requires explicit owner approval according to the configured durable approval record.

## Minimum adoption

For a small project, the practical minimum is:

- `GOVERNANCE.md`;
- `AGENTFLOW.md`;
- `DELIVERY-LIFECYCLE.md`;
- `AI-EXECUTION-RULES.md`;
- `templates/REQUIREMENT.md`;
- `templates/AGENT-TASK-CONTRACT.md`;
- `templates/EVIDENCE-BUNDLE.md`;
- `templates/INDEPENDENT-REVIEW.md`;
- a project-specific `PROJECT-ADAPTER.md`.

The exact normative process sequence and approval tokens are intentionally not duplicated here; see `GOVERNANCE.md`.

## Framework Core vs Project Adapter

### Core

Keep stable across projects:

- explicit scoped approvals;
- durable approval requirement;
- Architecture Delta Check;
- Development Analysis;
- Agent Task Contracts;
- retry limits and stop conditions;
- Evidence Bundles;
- candidate-bound Independent Review;
- immutable candidate identity;
- independent TEST;
- rollback-before-PROD;
- explicit PROD authorization;
- source-of-truth hierarchy;
- progressive context loading.

### Project Adapter

Configure per project:

- source-control platform;
- issue tracker;
- durable approval record location;
- branch strategy;
- CI/CD engine;
- environments;
- deployment platform;
- test executors;
- artifact identity mechanism;
- approval token mapping;
- architecture triggers specific to the system;
- security/compliance gates;
- owner vs multi-approver model.

## Applicability

AgentFlow works best when the target project has:

- a stable, inspectable project/repository state;
- a durable work/approval record;
- an immutable or equivalently verifiable candidate identity;
- a review mechanism;
- distinguishable DEV/TEST/PROD or equivalent promotion stages.

Projects that cannot establish candidate identity or durable approvals should treat bootstrap as `BLOCKED` until an equivalent control is defined.

## Versioning and compatibility

- Current version: see `VERSION`.
- Release changes: `CHANGELOG.md`.
- Consumer compatibility/adoption guidance: `COMPATIBILITY.md`.
- Canonical shipped-file inventory: `KIT-MANIFEST.md`.

Framework upgrades do **not** propagate automatically into consuming projects.

## Design intent

AgentFlow originated from a practical continuity problem: software work spread across multiple AI chats becomes difficult to resume safely.

Working principle:

> No information required for controlled continuation of the project should exist exclusively in a conversation.

See `docs/design/ORIGIN-AND-DESIGN-INTENT.md`.

## Non-goals

AgentFlow is not inherently:

- Scrum;
- SAFe;
- ITIL;
- a CAB process;
- a multi-person approval bureaucracy;
- a specific CI/CD platform;
- an AI vendor integration.

Use only controls justified by project risk and scale.

## License

No project license has been selected yet. Do not assume reuse/distribution terms until a license is explicitly added.
