# AgentFlow Delivery Framework — Independent Kit

Version: `1.1.0`
Status: `REFERENCE CORE`

## Purpose

AgentFlow is a lightweight software-delivery framework for projects where AI agents participate in requirements, architecture, implementation, review, testing, documentation, and release work.

The framework is designed to provide **high execution autonomy inside explicit decision boundaries**. It separates:

- what must be decided by a human owner or authorized approver;
- what an AI agent may analyze;
- what an AI agent may execute;
- what evidence must be produced;
- how implementation is independently reviewed;
- how one immutable candidate moves from DEV to TEST to PROD.

The framework is deliberately tool-neutral. GitHub, GitLab, Azure DevOps, Jira, Cloudflare, AWS, GCP, Azure, PostgreSQL, and specific AI products are adapters, not part of the Core.

## Start here

For framework use:

1. read `GOVERNANCE.md`;
2. read `AGENTFLOW.md`;
3. use `BOOTSTRAP-PROCEDURE.md` for a new target project;
4. generate a Project Adapter from `templates/PROJECT-ADAPTER.md`.

For framework development or a fresh AI session:

1. read `docs/PROJECT-CONTEXT-HANDOFF.md`;
2. read `docs/design/ORIGIN-AND-DESIGN-INTENT.md`;
3. load only the Core document relevant to the current task.

See `docs/INDEX.md` for the documentation map.

## Core principles

1. **Decide before coding.**
2. **Contract before execution.**
3. **Stop on material uncertainty.**
4. **Prove what was executed.**
5. **Review independently.**
6. **Promote one immutable candidate.**

## Kit structure

```text
AgentFlow_Framework/
├── README.md
├── VERSION
├── FRAMEWORK-CONFIG.md
├── BOOTSTRAP-PROCEDURE.md
├── GOVERNANCE.md
├── AGENTFLOW.md
├── DELIVERY-LIFECYCLE.md
├── DOCUMENTATION-POLICY.md
├── AI-EXECUTION-RULES.md
├── ADOPTION-GUIDE.md
├── agentflow.config.example.yaml
├── templates/
├── examples/
└── docs/
```

## Bootstrap a new project

Start with `BOOTSTRAP-PROCEDURE.md`. Bootstrap inspects the target project in read-only mode, builds the source-of-truth and gap maps, then proposes `PROJECT-ADAPTER.md`, `agentflow.config.yaml`, and `BOOTSTRAP-REPORT.md`.

Activate/persist the framework only after explicit owner approval.

## Minimum adoption

For a small project, adopt only:

- `GOVERNANCE.md`
- `AGENTFLOW.md`
- `DELIVERY-LIFECYCLE.md`
- `AI-EXECUTION-RULES.md`
- `templates/AGENT-TASK-CONTRACT.md`
- `templates/EVIDENCE-BUNDLE.md`
- `templates/INDEPENDENT-REVIEW.md`

Then create one project-specific adapter from `templates/PROJECT-ADAPTER.md`.

## Recommended flow

```text
IDEA
  ↓
REQUIREMENT ANALYSIS
  ↓
REQUIREMENT APPROVAL
  ↓
ARCHITECTURE GATE, if triggered
  ↓
DEVELOPMENT ANALYSIS
  ↓
TASK CONTRACT
  ↓
EXPLICIT TASK APPROVAL
  ↓
IMPLEMENTATION
  ↓
EVIDENCE BUNDLE
  ↓
INDEPENDENT REVIEW
  ↓
DEV PASS
  ↓
CANDIDATE FREEZE
  ↓
TEST PASS
  ↓
PROD GO
  ↓
PROD DEPLOY
  ↓
SMOKE PASS
  ↓
DONE
```

## Framework Core vs Project Adapter

### Core

Keep these concepts stable across projects:

- explicit approvals;
- Architecture Delta Check;
- Development Analysis;
- Agent Task Contracts;
- retry limits and stop conditions;
- Evidence Bundles;
- independent review;
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
- branch strategy;
- CI/CD engine;
- environments;
- deployment platform;
- test executors;
- artifact identity mechanism;
- approval syntax;
- architecture triggers specific to the system;
- security/compliance gates;
- owner vs multi-approver model.

## Design intent

The framework originated from a practical continuity problem: software work spread across multiple AI chats becomes difficult to resume safely.

The working design principle is:

> No information required for controlled continuation of the project should exist exclusively in a conversation.

This principle and the proposed Cold Start Test are documented in `docs/design/ORIGIN-AND-DESIGN-INTENT.md`. They are design records; changes to Core should still follow the framework's own decision process.

## Non-goals

AgentFlow is not inherently:

- Scrum;
- SAFe;
- ITIL;
- a CAB process;
- a multi-person approval bureaucracy;
- a specific CI/CD platform;
- an AI vendor integration.

Use only the controls justified by project risk and scale.

## License

No project license has been selected yet. Do not assume reuse/distribution terms until a license is explicitly added.
