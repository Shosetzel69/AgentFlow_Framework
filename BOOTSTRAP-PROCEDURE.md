# AgentFlow Bootstrap Procedure

Version: `1.1.1`
Status: `CANONICAL`
Applies to: new AgentFlow adoption

## 1. Purpose

Bootstrap converts an existing or greenfield software project into an AgentFlow-ready project without redesigning the product or silently changing its delivery process.

Bootstrap has one goal:

> Understand the project as it exists, map AgentFlow Core onto it, identify gaps, and generate the minimum project-specific configuration required for safe use.

Bootstrap is **read-only by default** with respect to application code, infrastructure, environments, production data, branch protection, CI/CD behavior, and external services.

It may create or update AgentFlow documentation/configuration only after the owner accepts the bootstrap result.

---

## 2. Inputs

Minimum input:

- project/repository location;
- project owner or authorized approver;
- whether the project is `GREENFIELD` or `EXISTING`.

Useful optional input:

- issue tracker;
- CI/CD platform;
- known environments;
- current architecture docs;
- current release/deploy procedure;
- security/compliance constraints;
- known legacy work in progress.

Do not require the owner to repeat information that can be verified from the project sources.

---

## 3. Bootstrap outputs

A successful bootstrap produces:

1. `PROJECT-ADAPTER.md` — project-specific mapping of AgentFlow Core;
2. `agentflow.config.yaml` — machine-readable project configuration;
3. `BOOTSTRAP-REPORT.md` — evidence, gaps, assumptions, decisions still required;
4. an adoption verdict:
   - `READY_TO_ADOPT`;
   - `READY_WITH_GAPS`;
   - `BLOCKED`.

Optional, only when explicitly approved:

- placement/copying of AgentFlow Core docs into the target repository;
- issue templates;
- AI instruction integration;
- CI policy checks;
- branch/release automation changes.

These optional actions are **not** part of read-only bootstrap discovery.

---

# 4. Bootstrap modes

## 4.1 GREENFIELD

Use when the project has no established delivery process or repository history that must be preserved.

Bootstrap may propose sensible defaults, but owner approval is required for:

- source-control strategy;
- environments;
- approval model;
- deployment model;
- architecture/documentation locations.

## 4.2 EXISTING

Use when the project already has code, CI/CD, issues, environments, release practices, or active work.

Primary rule:

> Adapt AgentFlow to the verified project before adapting the project to AgentFlow.

Do not mass-convert existing issues, documents, branches, or processes.

Classify existing work as:

- `AGENTFLOW` — new work or explicitly converted work;
- `LEGACY-ADAPTED` — materially started work kept on its existing process while using current release safety controls.

---

# 5. Phase B0 — Preflight

Confirm:

- target project/repository;
- access is sufficient for read-only inspection;
- bootstrap mode: `GREENFIELD | EXISTING`;
- project owner/approver identity or role;
- any explicit no-touch areas.

Record:

```text
Bootstrap mode:
Project:
Repository/repositories:
Owner model:
Read access:
Write authorization: NO by default
Excluded areas:
```

### Stop conditions

Return `BLOCKED` if:

- the target project cannot be identified;
- repository/project state cannot be inspected sufficiently;
- the owner model cannot be established;
- available evidence is too incomplete to distinguish current state from assumptions.

---

# 6. Phase B1 — Project inventory

Inspect only what is necessary to understand the delivery system.

## 6.1 Repository structure

Identify:

- repository/repositories;
- default/protected branches;
- application/component layout;
- infrastructure/configuration locations;
- documentation locations;
- test locations;
- deployment definitions.

## 6.2 Delivery tooling

Identify, where present:

- source-control provider;
- issue tracker;
- CI;
- CD/deployment mechanism;
- artifact/package registry;
- cloud/runtime;
- database/persistence;
- observability;
- secrets management;
- AI agents/connectors.

## 6.3 Environments

Map actual environments to AgentFlow roles:

| AgentFlow role | Existing project environment | Confidence |
|---|---|---|
| DEV | | |
| TEST | | |
| PROD | | |

Do not invent TEST if the project has only DEV/PROD. Record the gap.

## 6.4 Active work/process

For an existing project identify:

- active implementation work;
- open release candidates;
- work already in TEST/PROD promotion;
- legacy process documents still actively used.

Do not retroactively reclassify work without owner approval.

---

# 7. Phase B2 — Source-of-truth map

Determine where current truth lives.

Minimum subjects:

| Subject | Current source | Status |
|---|---|---|
| Requirements | | FOUND / MISSING / CONFLICT |
| Architecture | | |
| Data/API contracts | | |
| Delivery process | | |
| Release/deploy procedure | | |
| AI execution rules | | |
| Operational runbooks | | |

Rules:

- repository/project state outranks chat memory as evidence of implementation;
- approved canonical architecture/process outranks an agent's preferred redesign;
- if code and approved canonical documentation materially conflict, record `CONFLICT`; do not resolve silently;
- historical/superseded material is not treated as current simply because it exists.

---

# 8. Phase B3 — AgentFlow fit/gap analysis

Compare the verified project against AgentFlow Core.

Assess at minimum:

## Decision controls

- requirement approval;
- architecture gate;
- task execution approval;
- PROD authorization.

## Execution controls

- executable task/contract boundary;
- retry limit;
- stop conditions;
- evidence production;
- independent review.

## Release controls

- DEV verification;
- immutable candidate identity;
- independent TEST;
- rollback-before-PROD;
- exact candidate promotion;
- PROD smoke/release record.

## Context/documentation controls

- canonical source hierarchy;
- progressive context loading;
- documentation ownership;
- historical/current separation.

Use this classification:

```text
EXISTS     — project already satisfies the control
ADAPT      — equivalent mechanism exists and can be mapped
ADD        — control is missing but can be added without architecture change
DECIDE     — owner/architecture decision required
BLOCKED    — evidence/access/dependency prevents a safe conclusion
```

Produce a gap matrix:

| AgentFlow control | Current project | Classification | Required action |
|---|---|---|---|
| Requirement approval | | | |
| Architecture gate | | | |
| ATC/task contract | | | |
| Evidence bundle | | | |
| Independent review | | | |
| Candidate identity | | | |
| Independent TEST | | | |
| PROD GO | | | |
| Rollback | | | |

---

# 9. Phase B4 — Project Adapter generation

Generate `PROJECT-ADAPTER.md` from `templates/PROJECT-ADAPTER.md` using only verified facts and explicit decisions.

Rules:

- use `UNKNOWN` instead of inventing values;
- distinguish `CURRENT` from `TARGET` when adoption requires a transition;
- keep AgentFlow Core rules unchanged unless the owner explicitly approves a framework deviation;
- project-specific platform names belong in the adapter, not Core documents.

The adapter must define:

- owner/approval model;
- toolchain;
- repository/branch rules;
- environment mapping;
- candidate identity;
- approval tokens;
- project-specific architecture triggers;
- default ATC/evidence policy;
- review independence;
- rollback policy;
- canonical documentation map;
- legacy-transition rule if needed.

---

# 10. Phase B5 — Configuration generation

Generate `agentflow.config.yaml` from `agentflow.config.example.yaml`.

Only encode established values.

Example:

```yaml
framework:
  name: AgentFlow
  version: "1.1.1"

project:
  name: "example-project"
  process: AGENTFLOW
  legacy_transition: true

source_control:
  provider: github
  protected_branch: main
  direct_write_protected_branch: false
  candidate_identity: commit_sha
```

Unknown values remain explicit:

```yaml
environments:
  test: "UNKNOWN"
```

Do not hide unresolved decisions behind defaults.

---

# 11. Phase B6 — Adoption design

Determine the smallest safe adoption path.

## Greenfield default

```text
Core docs
→ Project Adapter
→ Config
→ repository/issue conventions
→ first Requirement
→ first AgentFlow delivery
```

## Existing project default

```text
new work → AGENTFLOW
materially started work → LEGACY-ADAPTED
single canonical release lifecycle
→ retire LEGACY-ADAPTED when last legacy item closes
```

Do not propose mass migration unless there is a concrete operational benefit.

Prioritize gaps in this order:

1. controls that prevent unsafe production changes;
2. source-of-truth conflicts;
3. architecture/authorization ambiguity;
4. executable contract/evidence gaps;
5. documentation/automation improvements.

---

# 12. Phase B7 — Bootstrap validation

Before declaring bootstrap complete, verify:

- every adapter value is verified, explicitly approved, or marked `UNKNOWN`;
- no project-specific rule leaked into AgentFlow Core;
- no existing active work was silently converted;
- no infrastructure/product/runtime mutation occurred during read-only bootstrap;
- unresolved architecture/security/privacy/cost questions are visible;
- adoption plan is minimal and reversible where possible;
- generated files do not contradict each other.

Run the consistency check:

```text
PROJECT-ADAPTER.md
      ↕
agentflow.config.yaml
      ↕
BOOTSTRAP-REPORT.md
```

Material contradictions result in `BLOCKED` until resolved.

---

# 13. Bootstrap verdict

## READY_TO_ADOPT

Use when:

- Core can be mapped without material unresolved decisions;
- project adapter/config are complete enough for the first AgentFlow work item;
- no safety-critical release control is missing or ambiguous.

## READY_WITH_GAPS

Use when:

- adoption can start safely;
- some non-critical controls remain to be added;
- gaps are explicitly tracked and do not permit unsafe execution.

## BLOCKED

Use when, for example:

- ownership/approval is ambiguous;
- current architecture/process truth is materially contradictory;
- production promotion cannot be bounded safely;
- candidate identity cannot be established;
- required access/evidence is missing.

---

# 14. Owner approval gate

Read-only bootstrap does not automatically activate AgentFlow in the target project.

Present:

- project adapter;
- config;
- bootstrap report;
- gap matrix;
- proposed adoption mode.

Recommended explicit approval:

```text
APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>
```

Only after approval may the project persist/activate the generated AgentFlow configuration and perform separately approved integration changes.

---

# 15. Post-bootstrap integration

After bootstrap approval, integration can be performed as one or more explicit tasks.

Typical integration tasks:

- add Core docs to repository/project handbook;
- add `PROJECT-ADAPTER.md`;
- add `agentflow.config.yaml`;
- add issue/task templates;
- add AI execution instructions;
- add documentation-policy checks;
- add branch/CI/CD safeguards;
- create first AgentFlow Requirement or Development Transfer.

Each integration task follows the project's newly approved AgentFlow process when practical.

Infrastructure/security changes require their normal architecture/change gates.

---

# 16. AI bootstrap execution contract

An AI executing bootstrap should use this sequence:

```text
B0 Preflight
→ B1 Project Inventory
→ B2 Source-of-Truth Map
→ B3 Gap Analysis
→ B4 Project Adapter
→ B5 Config
→ B6 Adoption Design
→ B7 Validation
→ Verdict
→ Owner Approval
```

During B0-B7 the AI must not:

- modify application code;
- deploy;
- change production data;
- alter branch protection;
- mutate CI/CD behavior;
- create paid resources;
- introduce dependencies;
- rewrite existing architecture/process decisions.

If the user explicitly asks bootstrap to also persist documentation, that write scope must be stated separately from discovery and must not silently include product/runtime changes.

---

# 17. Bootstrap prompt — reusable

Use this prompt with an AI agent that can inspect the target project:

```text
Bootstrap AgentFlow for this project.

Use AgentFlow BOOTSTRAP-PROCEDURE.md as the governing procedure.
Start in read-only mode.

Goals:
1. inspect the current project/repository and delivery setup;
2. build the source-of-truth map;
3. compare the project with AgentFlow Core;
4. identify EXISTS / ADAPT / ADD / DECIDE / BLOCKED gaps;
5. generate a proposed PROJECT-ADAPTER.md;
6. generate a proposed agentflow.config.yaml;
7. generate BOOTSTRAP-REPORT.md with evidence, assumptions, gaps and verdict;
8. propose the minimum adoption path.

Do not change code, infrastructure, CI/CD, environments, production data or branch protections during discovery.
Do not invent missing project facts; mark them UNKNOWN or DECIDE.
Do not mass-convert existing work.
Stop on material architecture/security/privacy/cost conflicts.

Return one verdict: READY_TO_ADOPT, READY_WITH_GAPS, or BLOCKED.
Do not activate/persist the framework until explicit owner approval.
```

---

# 18. Bootstrap completion checklist

- [ ] Mode selected: GREENFIELD / EXISTING
- [ ] Owner/approval model identified
- [ ] Repository/project inventory complete
- [ ] Toolchain identified
- [ ] DEV/TEST/PROD mapping assessed
- [ ] Source-of-truth map complete
- [ ] Active/legacy work assessed
- [ ] AgentFlow gap matrix complete
- [ ] PROJECT-ADAPTER.md generated
- [ ] agentflow.config.yaml generated
- [ ] BOOTSTRAP-REPORT.md generated
- [ ] Unknowns/decisions explicit
- [ ] No unauthorized runtime/product mutation
- [ ] Consistency check passed
- [ ] Bootstrap verdict recorded
- [ ] Owner approval obtained before activation
