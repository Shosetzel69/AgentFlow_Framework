# AgentFlow — External Audit Template

Document type: External Audit Request / Audit Report Structure  
Target: AgentFlow Delivery Framework  
Version audited: `<version>`  
Audit date: `<YYYY-MM-DD>`  
Auditor: `<name / organization>`  
Audit scope: `<scope summary>`

---

# 1. Auditor Role

Act as an independent external auditor for **AgentFlow Delivery Framework**.

The audit must be critical, evidence-based, and independent from the framework authors.

Do not modify:
- the framework;
- documentation;
- repositories;
- processes;
- implementation.

Do not assume that a documented rule is implemented or enforced.

For every relevant capability distinguish explicitly between:

- `DOCUMENTED`
- `IMPLEMENTED`
- `ENFORCED`
- `VERIFIED`
- `NOT VERIFIED`
- `MISSING`

---

# 2. Audit Objective

Evaluate whether AgentFlow is coherent, reusable, enforceable, and sufficiently controlled for AI-assisted software delivery.

The audit must determine:

1. whether the process model is coherent end-to-end;
2. whether roles and responsibilities are clear;
3. whether gates effectively prevent unauthorized execution;
4. whether Requirement, Architecture, Development, Review, TEST, and PROD are sufficiently separated;
5. whether Agent Task Contracts are sufficient for controlled execution;
6. whether Evidence Bundles support independent review;
7. whether the release lifecycle guarantees candidate identity and traceability;
8. whether fail-closed mechanisms are sufficient;
9. whether AgentFlow can be transferred to another project without hidden dependencies;
10. which risks and maturity gaps remain.

---

# 3. Scope

## 3.1 Governance

Evaluate:

- ownership;
- decision rights;
- explicit approvals;
- process transitions;
- canonical phase/status model;
- blocking semantics;
- escalation;
- separation of duties.

Findings:

`<auditor input>`

---

## 3.2 Requirements

Evaluate:

- idea -> requirement;
- approval;
- scope / out-of-scope;
- acceptance criteria;
- invariants;
- transfer to Development.

Findings:

`<auditor input>`

---

## 3.3 Architecture Governance

Evaluate:

- Architecture Delta Check;
- architecture triggers;
- ADR mechanism;
- owner approval;
- revalidation after architectural decisions;
- prevention of architecture-by-implementation.

Findings:

`<auditor input>`

---

## 3.4 Development Analysis

Evaluate:

- baseline verification;
- impact analysis;
- dependency analysis;
- slicing;
- risk identification;
- proposed ATCs;
- stop conditions.

Findings:

`<auditor input>`

---

## 3.5 Agent Task Contract

Evaluate whether ATCs define sufficiently:

- objective;
- scope;
- out-of-scope;
- dependencies;
- constraints;
- acceptance criteria;
- tests;
- retry limit;
- stop conditions;
- evidence requirements.

Findings:

`<auditor input>`

---

## 3.6 Agent Execution Controls

Evaluate:

- scope control;
- retry policy;
- escalation;
- no opportunistic refactoring;
- dependency introduction;
- architectural deviations;
- handling of ambiguity.

Findings:

`<auditor input>`

---

## 3.7 Evidence

Evaluate:

- Evidence Bundle completeness;
- reproducibility;
- traceability;
- mapping to Acceptance Criteria;
- residual risks;
- candidate identity.

Findings:

`<auditor input>`

---

## 3.8 Independent Review

Evaluate:

- independence;
- reviewer responsibilities;
- PASS / FAIL / BLOCKED semantics;
- prohibition of review-and-fix in the same activity;
- evidence sufficiency.

Findings:

`<auditor input>`

---

## 3.9 DEV / TEST / PROD Lifecycle

Evaluate:

- candidate freeze;
- immutable candidate;
- exact SHA/artifact identity;
- TEST independence;
- failure return to DEV;
- PROD approval;
- rollback;
- smoke validation;
- release record.

Findings:

`<auditor input>`

---

## 3.10 Documentation / Source of Truth

Evaluate:

- canonical document hierarchy;
- precedence;
- current vs historical information;
- progressive context loading;
- duplicate source-of-truth risks;
- auditability.

Findings:

`<auditor input>`

---

## 3.11 Security and Privacy

Evaluate both existing controls and missing capabilities:

- security gates;
- secrets handling;
- privilege boundaries;
- security acceptance;
- threat modeling;
- dependency/security scanning;
- privacy controls.

Findings:

`<auditor input>`

---

## 3.12 Operational Model

Evaluate coverage or gaps for:

- monitoring;
- incident management;
- rollback;
- post-release observation;
- operational ownership;
- capacity/cost controls.

Findings:

`<auditor input>`

---

## 3.13 Multi-Agent Readiness

Evaluate:

- agent identity;
- role separation;
- handoffs;
- concurrency;
- task locking;
- duplicate execution;
- provenance;
- recovery after agent failure.

Findings:

`<auditor input>`

---

## 3.14 Portability

Determine whether AgentFlow Core is independent of:

- GitHub;
- specific CI/CD tools;
- specific cloud providers;
- specific AI models;
- specific databases;
- specific project structures.

Findings:

`<auditor input>`

---

# 4. Out of Scope

Unless explicitly requested, do not evaluate:

- business value of the product using AgentFlow;
- code quality of unrelated application code;
- performance of individual AI models;
- comparison of cloud providers;
- Scrum/SAFe compliance;
- project-specific implementation details that are not part of AgentFlow Core.

Additional exclusions:

`<auditor input>`

---

# 5. Evidence Standard

For every material conclusion provide:

```text
Claim:
Evidence:
Evidence source:
Verification method:
Confidence:
```

Confidence values:

- `HIGH`
- `MEDIUM`
- `LOW`

Do not classify a capability as implemented merely because it is documented.

Use the maturity distinction:

```text
DEFINED
IMPLEMENTED
ENFORCED
VERIFIED
```

Example:

```text
Rule: Task Contract approval required

Defined: YES
Implemented: YES
Enforced automatically: NO
Verified against real execution: YES
```

---

# 6. Audit Method

Use this sequence:

```text
1. Inventory
2. Source-of-truth validation
3. Process reconstruction
4. Control identification
5. Evidence verification
6. Failure-path analysis
7. Portability analysis
8. Gap analysis
9. Maturity assessment
10. Recommendations
```

Do not begin with recommendations.

Establish AS-IS first.

---

# 7. Required Challenge Scenarios

## Scenario 1 — Scope Creep

Situation:

During implementation, an agent identifies an adjacent improvement.

Audit question:

> Does AgentFlow reliably prevent silent inclusion?

Evidence / result:

`<auditor input>`

---

## Scenario 2 — Architecture Change Discovered During DEV

Situation:

Implementation requires a new datastore, shared API contract, or architectural boundary change.

Audit question:

> Does execution stop and return to Architecture?

Evidence / result:

`<auditor input>`

---

## Scenario 3 — Missing Approval

Situation:

An ATC exists but has not been explicitly approved.

Audit question:

> Can implementation proceed?

Evidence / result:

`<auditor input>`

---

## Scenario 4 — Retry Exhaustion

Situation:

Mandatory tests still fail after configured retry limits.

Audit question:

> Does the process fail closed?

Evidence / result:

`<auditor input>`

---

## Scenario 5 — Reviewer Discovers a Defect

Audit question:

> Is review clearly separated from remediation?

Evidence / result:

`<auditor input>`

---

## Scenario 6 — Candidate Mutation After TEST

Situation:

Code changes after TEST PASS.

Audit question:

> Is previous TEST evidence invalidated?

Evidence / result:

`<auditor input>`

---

## Scenario 7 — PROD Failure

Situation:

Smoke validation fails after deployment.

Audit question:

> Is rollback predetermined and is remediation returned to DEV?

Evidence / result:

`<auditor input>`

---

## Scenario 8 — Documentation Conflict

Situation:

Repository state contradicts canonical architecture documentation.

Audit question:

> Does the framework provide a deterministic handling rule?

Evidence / result:

`<auditor input>`

---

## Scenario 9 — Multi-Agent Collision

Situation:

Two agents attempt overlapping work.

Audit question:

> Does AgentFlow currently prevent or resolve the collision?

Evidence / result:

`<auditor input>`

---

## Scenario 10 — Adoption in Another Project

Situation:

AgentFlow is conceptually applied to an unrelated repository.

Audit question:

> Which Core rules transfer directly and which require adapters?

Evidence / result:

`<auditor input>`

---

# 8. Finding Classification

Each finding must use this structure.

## Finding `<ID>`

**Domain:** `<domain>`

**Title:** `<short title>`

**Severity:**

`CRITICAL | HIGH | MEDIUM | LOW | OBSERVATION`

**Type:**

`DESIGN_GAP | CONTROL_GAP | ENFORCEMENT_GAP | DOCUMENTATION_GAP | TRACEABILITY_GAP | SECURITY_GAP | OPERATIONAL_GAP | SCALABILITY_GAP`

**Evidence:**

`<evidence>`

**Why it matters:**

`<impact>`

**Failure scenario:**

`<scenario>`

**Recommendation:**

`<recommendation>`

**Required before:**

`NOW | NEXT_MINOR | NEXT_MAJOR | ENTERPRISE_ONLY | OPTIONAL`

---

# 9. Required Audit Output

## 9.1 Executive Summary

Maximum 1–2 pages.

Include:

- overall assessment;
- strongest controls;
- largest risks;
- intended use cases where AgentFlow is currently suitable;
- contexts where it is not sufficient without extensions.

Executive Summary:

`<auditor input>`

---

## 9.2 Coverage Matrix

| Domain | Defined | Implemented | Enforced | Verified | Main Gap |
|---|---|---|---|---|---|
| Requirements | | | | | |
| Architecture | | | | | |
| Development Analysis | | | | | |
| ATC | | | | | |
| Evidence | | | | | |
| Review | | | | | |
| DEV / TEST / PROD | | | | | |
| Documentation | | | | | |
| Security | | | | | |
| Operations | | | | | |
| Multi-agent | | | | | |
| Portability | | | | | |

---

## 9.3 Control Effectiveness

| Control | Purpose | Failure Prevented | Enforcement | Evidence | Effectiveness |
|---|---|---|---|---|---|
| | | | | | |

Do not rate effectiveness without evidence.

---

## 9.4 Findings

List all findings here.

Order:

1. severity;
2. dependency;
3. execution priority.

`<auditor input>`

---

## 9.5 Maturity Assessment

Assess separately:

### Process Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Governance Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Architecture Governance Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Agent Execution Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Evidence / Traceability Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Release Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Automation / Enforcement Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Multi-Agent Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Operations Maturity

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

### Enterprise Readiness

Current state:

`<auditor input>`

Evidence:

`<auditor input>`

Main limitation:

`<auditor input>`

Next maturity threshold:

`<auditor input>`

---

# 10. Core vs Adapter Assessment

## 10.1 Appropriate for Core

Capabilities that should exist in every AgentFlow deployment:

`<auditor input>`

---

## 10.2 Appropriate for Project Adapter

Tool/project-specific behavior:

`<auditor input>`

---

## 10.3 Appropriate for Organization Adapter

Enterprise/security/compliance-specific behavior:

`<auditor input>`

---

## 10.4 Layering Problems

Capabilities currently placed in the wrong layer:

`<auditor input>`

---

# 11. Missing Controls

## Required for Current Target Users

`<auditor input>`

## Required for Scaling

`<auditor input>`

## Required for Enterprise

`<auditor input>`

## Optional

`<auditor input>`

---

# 12. Recommended Roadmap

## Immediate

Problems affecting current correctness or safety:

`<auditor input>`

---

## Next Minor Version

Improvements strengthening the current framework without changing its fundamental model:

`<auditor input>`

---

## Next Major Version

Capabilities requiring architectural change to AgentFlow itself:

`<auditor input>`

---

## Enterprise Extensions

Controls unnecessary for Core but needed by larger organizations:

`<auditor input>`

---

# 13. Independence Requirements

The auditor must:

- challenge assumptions;
- report contradictory evidence;
- distinguish framework claims from verified behavior;
- avoid treating documentation volume as evidence of maturity;
- avoid recommending enterprise bureaucracy unless justified by identified risk;
- avoid optimizing for the original source project;
- evaluate AgentFlow as an independent reusable framework.

Independence concerns identified:

`<auditor input>`

---

# 14. Final Audit Conclusion

## Current Suitable Use

`<contexts>`

## Current Unsuitable Use

`<contexts>`

## Material Blockers

`<list or NONE>`

## Highest-Priority Improvement

`<item>`

## Evidence Confidence

`HIGH | MEDIUM | LOW`

## Final Notes

`<auditor input>`

---

# 15. Audit Sign-Off

Auditor:

`<name>`

Organization:

`<organization>`

Date:

`<YYYY-MM-DD>`

Audit version / reference:

`<reference>`
