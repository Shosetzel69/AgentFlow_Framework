# AgentFlow Metrics Catalogue

Status: `REFERENCE CORE`  
Document version: `1.1.0`  
Framework compatibility: `1.3.x`

## 1. Purpose

This catalogue defines a minimal common metric vocabulary. AgentFlow v1.3 remains tool-neutral: measurement may be manual or project-specific and does not imply a metrics engine.

## 2. Delivery metrics

| Metric | Definition |
|---|---|
| Requirement-to-PROD lead time | durable Requirement Approval to successful PROD smoke/closure |
| ATC cycle time | durable ATC approval to implementation/evidence ready |
| First-pass review success | reviewed candidates receiving REVIEW_PASS without remediation |
| Remediation cycles per ATC | returns to implementation after REVIEW_FAIL or TEST_FAIL |
| Architecture escalation frequency | work items returning to Architecture Gate |
| TEST failure rate | candidate TEST executions resulting in TEST_FAIL |
| Rollback rate | production releases requiring rollback |
| Forward-fix rate | production failures using approved forward-fix |
| Blocked time by phase | time in phase-specific BLOCKED state |
| Approval wait time | gate-ready state to durable approval |

## 3. Execution-context metrics

**AgentFlow-controlled execution context** means the ATC, applicable execution rules, and process/project documentation explicitly declared or loaded because of AgentFlow context policy.

It excludes implementation-driven source/code exploration.

| Metric | Definition |
|---|---|
| Declared execution context size | deterministic characters/bytes calculated at authoring from the DA-declared initial execution packet |
| Estimated execution-context tokens | informational estimate derived from declared/actual controlled context |
| Actual initial controlled context | controlled context actually loaded before implementation exploration |
| Context expansion size | additional controlled context loaded after start |
| Largest controlled read | largest single controlled document/section read |
| Full-document reads | count/size of controlled full-document reads |
| Execution-rules size | character/byte size of `AI-EXECUTION-RULES.md` for the shipped version |
| Reference-scenario overhead | controlled-context size for the frozen versioned reference scenario |
| Context overhead regression | same-scenario delta between framework releases |

Reference goals for normal execution:
- normal declared controlled context: <5k estimated tokens;
- stretch: <3k estimated tokens;
- `AI-EXECUTION-RULES.md` v1.3 target: ≤7,000 characters.

A threshold miss requires explicit reduction, re-slicing or justified disposition; it is not an automatic runtime gate.

## 4. Reference scenario discipline

A reference scenario has an independent ID/version. Changing its semantics requires a new scenario version and explicit baseline reset. Different scenario versions are not silently compared.

## 5. Collection and gate response expectations

Metrics may be collected manually or with project-specific tooling. Do not claim framework-level automation unless it exists.

Project Adapter may define response-time expectations for approvals/review. Expiry never grants authority.

## 6. Future automation boundary

Automatic collection/enforcement from machine-readable workflow state remains future executable-framework work.
