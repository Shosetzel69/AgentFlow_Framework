# AgentFlow Bootstrap Procedure

Document version: `1.2.0`  
Status: `CANONICAL`  
Framework compatibility: `1.2.x`  
Applies to: new AgentFlow adoption and revalidation

## 1. Purpose

Bootstrap converts an existing or greenfield software project into an AgentFlow-ready project without redesigning the product or silently changing its delivery process.

Bootstrap is read-only by default with respect to application code, infrastructure, environments, production data, branch protection, CI/CD behavior, and external services.

It may persist/activate AgentFlow configuration only after `APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>` is durably recorded.

## 2. Inputs

Minimum:

- project/repository/change-system location;
- project owner or authorized approver;
- `GREENFIELD` or `EXISTING`;
- durable approval-record system/location, or explicit `DECIDE` gap;
- candidate/artifact identity mechanism, or explicit `DECIDE` gap.

## 3. Applicability preflight

Before inventory, determine whether the target can satisfy:

1. durable project/change record;
2. durable approval record;
3. immutable or equivalently verifiable candidate/artifact identity;
4. change-review mechanism;
5. inspectable delivery state/tooling.

If any cannot be established or mapped to an equivalent control, return `BLOCKED`.

Non-git delivery is allowed only when an equivalent immutable snapshot/export/package/hash identity is defined.

## 4. Outputs

Bootstrap produces:

1. `PROJECT-ADAPTER.md`;
2. `agentflow.config.yaml`;
3. `BOOTSTRAP-REPORT.md`;
4. adoption verdict: `READY_TO_ADOPT | READY_WITH_GAPS | BLOCKED`.

## 5. Modes

### GREENFIELD

Adopt AgentFlow directly after bootstrap approval.

### EXISTING

Default transition:

- new work → `AGENTFLOW`;
- materially started work → `LEGACY-ADAPTED`.

Do not mass-convert existing work.

## 6. Project inventory

Identify only what is necessary:

- repositories/change systems;
- branches or equivalent change-review mechanism;
- application/component layout;
- docs/tests/deployment definitions;
- issue/work tracker;
- CI/CD;
- runtime/cloud;
- persistence;
- observability;
- secrets/access management;
- AI agents/connectors;
- environments;
- current active/release work.

## 7. Source-of-truth map

Minimum:

| Subject | Current source | Status |
|---|---|---|
| Requirements | | FOUND / MISSING / CONFLICT |
| Architecture | | |
| Data/API contracts | | |
| Delivery process | | |
| Approval records | | |
| Artifact/candidate identity | | |
| Release/deploy procedure | | |
| AI execution rules | | |
| Operational runbooks | | |

Repository/project state outranks chat memory as implementation evidence.

## 8. Fit/gap analysis

Use:

`EXISTS | ADAPT | ADD | DECIDE | BLOCKED`

Assess at minimum:

### Decision controls

- bootstrap approval;
- Requirement Approval;
- durable approval record;
- Architecture Gate;
- ATC Approval;
- PROD authorization;
- production-data exception approval;
- forward-fix authorization.

### Execution controls

- Development Analysis artifact;
- executable ATC boundary;
- per-execution retry limit;
- remediation-cycle budget;
- single-active-executor/handoff;
- stop conditions;
- evidence classes;
- Independent Review level/binding.

### Release controls

- DEV verification;
- Candidate Manifest;
- immutable candidate identity;
- independent TEST;
- rollback/recovery;
- exact candidate promotion;
- PROD smoke/release record.

### Access/privacy controls

- phase-scoped environments;
- credential-role boundaries;
- production-data-in-nonPROD rule.

### Context/documentation controls

- canonical source hierarchy;
- artifact identity/parent links;
- progressive context;
- current/history separation.

## 9. Project Adapter generation

Generate from `templates/PROJECT-ADAPTER.md`.

Use only verified facts and explicit decisions.

The Adapter must include:

- ownership/approval model;
- toolchain;
- durable record locations;
- artifact ID mapping;
- environment/candidate mapping;
- phase access boundaries;
- approval tokens;
- project-specific architecture triggers;
- execution/evidence/review policy;
- release/recovery;
- production-data handling;
- canonical documentation map;
- legacy transition;
- metrics/gate expectations;
- last validated / revalidation triggers;
- outstanding gaps with owner and closure condition.

## 10. Machine-readable configuration

Generate `agentflow.config.yaml` from the example.

Rules:

- config is authoritative for machine-readable values;
- Adapter is authoritative for rationale/human mapping;
- values represented in both must match;
- material mismatch => `BLOCKED`;
- unknown values remain explicit, never hidden behind defaults.

## 11. Gap ownership and closure

Every `READY_WITH_GAPS` item records:

- gap ID/description;
- owner;
- accepted temporary condition;
- closure condition;
- target/revalidation trigger.

A gap without owner or closure condition is not acceptable as `READY_WITH_GAPS`; use `BLOCKED`.

## 12. Revalidation

Bootstrap output is not permanent.

Revalidation is required after any of:

- environment topology change;
- source-control/change-system change;
- CI/CD or deployment mechanism change;
- ownership/approval model change;
- durable approval record change;
- candidate identity mechanism change;
- phase credential/access-boundary change;
- AgentFlow framework version outside declared compatible range.

Project Adapter records:

- last validated date;
- validated framework version;
- next revalidation triggers.

Revalidation may be focused on affected sections but must re-run consistency checks.

## 13. Validation

Before completion verify:

- applicability preconditions pass;
- every Adapter/config value is verified, approved, or explicitly unresolved;
- durable approval record configured;
- candidate identity established;
- phase access map exists;
- review independence level >= Core minimum;
- no project-specific rule leaked into Core;
- no active work silently converted;
- no unauthorized runtime/product mutation;
- unresolved material security/privacy/cost/architecture questions visible;
- Adapter/config/report do not materially contradict each other.

## 14. Verdicts

### READY_TO_ADOPT

Use only when safety-critical controls and applicability preconditions are established.

### READY_WITH_GAPS

Use only for non-critical gaps that have an owner and closure condition.

### BLOCKED

Use when, for example:

- approval/ownership ambiguous;
- candidate identity unavailable;
- change-review mechanism unavailable;
- durable approval record unavailable;
- phase access boundary cannot be established;
- current architecture/process truth materially conflicts;
- required access/evidence is insufficient.

## 15. Owner approval gate

Recommended command:

`APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>`

The approval must be persisted in the configured durable approval record.

It authorizes persistence/activation of approved AgentFlow configuration only. It does not authorize application/runtime/infrastructure changes.

## 16. Post-bootstrap integration

Integration changes are separate explicit work items.

Typical tasks:

- persist Core docs/Adapter/config;
- add task templates;
- add AI execution instructions;
- add project-specific policy checks;
- configure branch/change protections.

Infrastructure/security/runtime changes use their normal gates.

## 17. Completion checklist

- [ ] Mode selected
- [ ] Applicability preconditions passed
- [ ] Owner/approval model identified
- [ ] Durable approval record identified
- [ ] Immutable candidate/artifact identity established
- [ ] Repository/change-system inventory complete
- [ ] Toolchain/environment mapping assessed
- [ ] Phase access/credential roles mapped
- [ ] Source-of-truth map complete
- [ ] AgentFlow gap matrix complete
- [ ] Gaps have owner + closure condition
- [ ] Project Adapter generated
- [ ] agentflow.config.yaml generated
- [ ] Adapter/config consistency passed
- [ ] Review independence level selected
- [ ] Revalidation metadata recorded
- [ ] No unauthorized product/runtime mutation
- [ ] Bootstrap verdict recorded
- [ ] Bootstrap approval durably recorded before activation
