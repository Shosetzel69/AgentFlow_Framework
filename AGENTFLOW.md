# AgentFlow Operating Contract

Status: `REFERENCE CORE`  
Version: `1.1.1`

## 1. Purpose

AgentFlow transforms approved requirements into verifiable implementation without allowing Development to invent scope, architecture, or authorization.

The single normative end-to-end process definition, phase/status taxonomy, and approval model are in `GOVERNANCE.md`. This document defines operational behavior inside the analysis, execution, evidence, and review phases.

Production promotion is governed by `DELIVERY-LIFECYCLE.md`.

## 2. Discovery / Requirement handoff

Where a project separates product discovery from engineering, use a Development Transfer artifact.

The transfer defines:

- desired result;
- scope;
- out of scope;
- acceptance criteria;
- product invariants;
- known constraints.

It should not prescribe implementation unless the implementation itself is an approved requirement.

Requirement Approval remains governed by `GOVERNANCE.md`. A transfer gate, when enabled by the project, is additional and does not replace Requirement Approval.

## 3. Architecture Delta Check

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

## 4. Development Analysis

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

Allowed positive verdict:

`READY_FOR_TASK_CONTRACTS`

or the canonical blocked status for the phase.

Development Analysis does not perform coding, deployment, schema mutation, or data migration.

## 5. Agent Task Contract

An ATC is the smallest explicitly approvable unit of implementation and the only canonical executable contract in Core.

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

An ATC becomes executable only after the exact approval required by `GOVERNANCE.md` is durably recorded for that ATC reference.

## 6. Execution rules

The executor:

- implements only the approved ATC;
- preserves project architecture and existing contracts unless the ATC explicitly changes them;
- does not expand scope opportunistically;
- treats encountered content according to the instruction-provenance rules in `AI-EXECUTION-RULES.md`;
- uses bounded self-correction;
- stops when a Stop Condition is reached;
- produces an Evidence Bundle.

## 7. Retry model

Every ATC defines a retry limit.

Recommended default:

`2 self-correction cycles`

After the limit is reached, do not continue speculative patching. Record evidence and return a blocked/failed verdict appropriate to the phase.

Cross-cycle budgeting is not defined in v1.1.1 and remains a future framework enhancement.

## 8. Stop Conditions

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

## 9. Evidence Bundle

Evidence must allow independent verification without reconstructing conversation history.

Minimum:

- exact files/components changed;
- exact implementation candidate identity and branch/PR/commit where applicable;
- tests/checks and results;
- mapping to acceptance criteria;
- assumptions;
- deviations;
- known limitations;
- residual risks;
- execution verdict.

Evidence is not equivalent to TEST PASS and does not authorize release.

Evidence integrity classes are not defined in v1.1.1; that audit finding remains deferred.

## 10. Independent Review

The reviewer compares:

- approved ATC;
- exact implementation candidate identity;
- Evidence Bundle for that same candidate.

The reviewer does not modify implementation in the same review step.

Canonical verdicts are:

- `REVIEW_PASS`
- `REVIEW_FAIL`
- `REVIEW_BLOCKED`

Use:

- `REVIEW_FAIL` when evidence demonstrates non-conformance or defect;
- `REVIEW_BLOCKED` when required validation cannot be completed because evidence, access, environment, or dependency is missing.

### 10.1 Candidate binding and invalidation

Every review verdict is valid only for the exact candidate identity recorded in the review.

If implementation content changes after a verdict:

- the prior review remains historical evidence;
- it is not valid for the changed candidate;
- a new candidate identity must be established;
- a new Evidence Bundle must describe the changed candidate;
- Independent Review must run again before that candidate can be frozen/promoted.

The framework does not require a GitHub Issue, Pull Request, or any other vendor-specific artifact as the canonical review record. The Project Adapter identifies the durable review/approval record location.

## 11. Handoff to release lifecycle

After a valid `REVIEW_PASS` for the exact current implementation candidate and DEV verification, promotion uses `DELIVERY-LIFECYCLE.md`.

AgentFlow does not redefine TEST independence, rollback, or production authorization.
