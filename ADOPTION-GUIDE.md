# AgentFlow Adoption Guide

Status: `NON-NORMATIVE ADOPTION GUIDE`  
Framework compatibility: `1.2.x`

> This guide explains adoption. It does not redefine the normative AgentFlow process; use `GOVERNANCE.md` for process/status/approval rules.

## 1. Start with bootstrap

Run `BOOTSTRAP-PROCEDURE.md`.

Do not activate AgentFlow until:

- applicability preconditions pass;
- durable approval location is configured;
- immutable/equivalent candidate identity exists;
- Project Adapter and config agree;
- required phase access boundaries are mapped;
- `APPROVE_AGENTFLOW_BOOTSTRAP <project-ref>` is durably recorded.

## 2. Greenfield

Adopt AgentFlow directly after bootstrap approval.

## 3. Existing project

Do not retrofit every old work item.

Default transition:

- new work → `AGENTFLOW`;
- materially started old work → `LEGACY-ADAPTED`.

Use one release lifecycle.

## 4. Minimum v1.2 control set

Before the first normal implementation verify:

- Requirement approval token and durable record;
- Development Analysis template/location;
- ATC approval token;
- retry limit + remediation-cycle budget;
- evidence minimum class;
- review independence level;
- Candidate Manifest;
- immutable candidate identity;
- TEST mapping;
- rollback/forward-fix recovery path;
- PROD GO token;
- executor provenance/handoff;
- phase access boundaries;
- artifact ID mapping;
- revalidation metadata.

## 5. AI-heavy mode

Strengthen:

- exact artifact references;
- required evidence class;
- candidate identity binding;
- executor/session provenance;
- context limits;
- access/credential scoping;
- Project Adapter revalidation.

Do not compensate for uncertain AI behavior by loading entire project history.

## 6. Upgrade from v1.1

Read:

- `CHANGELOG.md`;
- `COMPATIBILITY.md`;
- `docs/reference/CORE-VERSION-MATRIX.md`.

Do not overwrite local Project Adapter/config values with templates. Reconcile the new fields explicitly and revalidate the adapter.

## 7. What remains future work

v1.2 does not provide:

- state machine;
- automatic gate enforcement;
- lock manager;
- multi-agent scheduler/orchestrator;
- automated artifact graph;
- automated metrics.

Do not claim those capabilities from documentation alone.
