# AgentFlow Operating Contract

Status: `REFERENCE CORE`
Version: `1.0.0`

## 1. Purpose

AgentFlow transforms approved requirements into verifiable implementation without allowing Development to invent scope, architecture, or authorization.

AgentFlow governs the path from approved requirement through implementation review. Production promotion is governed by `DELIVERY-LIFECYCLE.md`.

## 2. Nominal flow

```text
approved requirement
→ APPROVE_TRANSFER, if a formal transfer gate is used
→ Architecture Gate, if triggered
→ Development Analysis
→ READY_FOR_TASK_CONTRACTS
→ Agent Task Contract
→ APPROVE_TASK_CONTRACT
→ Implementation
→ Evidence Bundle
→ Independent Review
→ DEV verification
→ Delivery Lifecycle
```

Development Analysis and execution are separate phases.

## 3. Discovery / Requirement handoff

Where a project separates product discovery from engineering, use a Development Transfer artifact.

The transfer defines:

- desired result;
- scope;
- out of scope;
- acceptance criteria;
- product invariants;
- known constraints.

It should not prescribe implementation unless the implementation itself is an approved requirement.

## 4. Architecture Delta Check

Before proposing an executable ATC, Development Analysis compares the requested change against current approved architecture.

Architecture Gate is mandatory when the implementation requires or assumes a material change to:

- datastore/persistence;
- data ownership/source of truth;
- identity/authentication/authorization/tenancy;
- component boundaries;
- shared APIs/contracts;
- orchestration/scheduler/concurrency;
- infrastructure/provider/framework with architectural role;
- security/privacy/secrets;
- material cost or exit/portability model.

When triggered:

1. stop executable planning for the affected part;
2. mark the current phase blocked;
3. identify the architecture question;
4. Architecture evaluates options and consequences;
5. authorized approver decides;
6. Development Analysis revalidates affected assumptions and ATCs.

Development may describe the problem and options. It does not silently make the architecture decision.

## 5. Development Analysis

Development Analysis is read-only relative to product/runtime state.

Minimum output:

- verified technical baseline;
- affected components;
- dependencies;
- Architecture Delta Check;
- implementation slicing;
- risks;
- Proposed Agent Task Contracts;
- stop conditions;
- verdict.

Allowed verdicts:

```text
READY_FOR_TASK_CONTRACTS
```

or the canonical blocked status for the phase.

Development Analysis does not perform coding, deployment, schema mutation, or data migration.

## 6. Agent Task Contract

An ATC is the smallest explicitly approvable unit of implementation.

Minimum fields:

- stable ID/reference;
- parent requirement/analysis;
- objective;
- scope;
- out of scope;
- required context;
- dependencies;
- constraints;
- acceptance criteria;
- tests;
- retry limit;
- stop conditions;
- required evidence.

An ATC becomes executable only after explicit approval for that exact reference.

## 7. Execution rules

The executor:

- implements only the approved ATC;
- preserves project architecture and existing contracts unless the ATC explicitly changes them;
- does not expand scope opportunistically;
- uses bounded self-correction;
- stops when a Stop Condition is reached;
- produces an Evidence Bundle.

## 8. Retry model

Every ATC defines a retry limit.

Recommended default:

```text
2 self-correction cycles
```

After the limit is reached, do not continue speculative patching. Record evidence and return a blocked/failed verdict appropriate to the phase.

## 9. Stop Conditions

Stop and escalate when a material issue appears in any of these categories:

- requirement change;
- scope expansion;
- acceptance-criteria change;
- business ambiguity with materially different outcomes;
- requirement vs architecture contradiction;
- architectural service/provider/runtime change;
- breaking shared API or persistent model;
- unauthorized data migration;
- dependency with material cost/security/licensing/operational impact;
- security/privacy concern requiring explicit acceptance;
- missing access/credentials required for execution;
- mandatory tests still failing after retry limit.

Do not escalate purely local, reversible, in-scope implementation choices that remain compatible with approved architecture.

## 10. Evidence Bundle

Evidence must allow independent verification without reconstructing conversation history.

Minimum:

- exact files/components changed;
- exact candidate/branch/PR/commit where applicable;
- tests/checks and results;
- mapping to acceptance criteria;
- assumptions;
- deviations;
- known limitations;
- residual risks;
- execution verdict.

Evidence is not equivalent to TEST PASS and does not authorize release.

## 11. Independent Review

The reviewer compares:

```text
Approved ATC
+ exact implementation candidate
+ Evidence Bundle
```

The reviewer does not modify implementation in the same review step.

Canonical verdicts:

- `REVIEW_PASS`
- `REVIEW_FAIL`
- `REVIEW_BLOCKED`

Use:

- `FAIL` when evidence demonstrates non-conformance or defect;
- `BLOCKED` when required validation cannot be completed because evidence, access, environment, or dependency is missing.

## 12. Handoff to release lifecycle

After Review and DEV verification, promotion uses `DELIVERY-LIFECYCLE.md`.

AgentFlow does not redefine candidate identity, TEST independence, rollback, or production authorization.
