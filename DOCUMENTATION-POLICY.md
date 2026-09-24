# AgentFlow Documentation Policy

Status: `REFERENCE CORE`  
Document version: `1.3.0`  
Framework compatibility: `1.3.x`

## 1. Goal

Documentation must reduce execution risk without becoming execution overhead.

Core rule:

> Read and maintain only the context required for the current task.

Authoring may spend broader context to make execution smaller and deterministic.

## 2. Documentation layers

### L0 — Entry / Handoff
Work items, PR/MR/change descriptions and release handoffs. They point to authoritative detail.

### L1 — Canonical Current State
Governance, approved architecture/requirements/contracts, AgentFlow Core, Adapter/config.

### L2 — Operational Procedures
Runbooks, migration/cutover and QA/test procedures.

### L3 — Reference / History
Analyses, reports, audits, research, superseded material and archived procedures.

L3 is excluded from normal execution context unless the exact task explicitly needs it.

## 3. Authoring context vs execution context

Requirement, Architecture and Development Analysis may inspect broader context needed to decide and slice work.

Development Analysis distills that context into an `Execution Context` for every proposed ATC.

Normal executor preload is limited to:
1. exact approved ATC;
2. applicable `AI-EXECUTION-RULES.md`;
3. exact project/source context declared for that ATC.

Parent Requirement/DA/ADR remain authoritative traceability/authoring records but are not normal full-text executor preload.

## 4. Execution Context contract

Every proposed ATC has:

```text
Required:
- exact files/sections/ranges needed before execution

Optional:
- exact source
- named condition/question that permits loading it

Excluded:
- task-specific exclusions

Pre-execution size:
- deterministic characters/bytes
- informational estimated tokens
```

Prefer section/heading/range references over full-document references.

A full-document read is exceptional when a narrower range can answer the question.

## 5. Default execution exclusions

Unless explicitly required, exclude:
- prior conversation/chat history;
- full work-item/comment history;
- audits and research;
- superseded/historical analysis;
- unrelated Requirements/ADRs/ATCs;
- unrelated Core/reference documentation.

Exclusions are semantic, not directory-based. A project may keep canonical execution-relevant documentation under `docs/`.

## 6. Context expansion

Missing execution authority is not a context-expansion trigger. It is a contract/readiness defect and requires STOP.

Missing project/source detail may use bounded targeted expansion:
- smallest exact source/section needed;
- only for a named unresolved implementation question;
- no implied scope or authority expansion.

## 7. Durable analysis and checkpoints

Material process state required for controlled continuation must not exist only in conversation.

Persist a completed material analysis unit before relying on it for canonical readiness/approval state, and persist material unrecorded outcomes before topic/chat/phase/role transition.

Minimal checkpoint:
- Findings
- Decision / disposition
- Evidence
- Open / blocked
- Next

Do not persist full transcripts merely to satisfy this rule.

If durable persistence is unavailable, mark persistence pending and do not claim canonical completion/readiness supported only by transient conversation.

## 8. Current state vs history

After a decision:
- keep the durable outcome/reference;
- update canonical current-state documentation;
- preserve analysis/history separately;
- do not create a second current-state manual from historical analysis.

## 9. Update discipline

Prefer one canonical source, references from secondary locations, and archive/supersession for obsolete material.

Avoid copy/paste synchronization, competing current truths, documentation-only churn, and documents created solely for ceremony.

## 10. Versioning and self-consistency

Canonical documents keep stable paths and use version-control history for old versions. Shipped versions are recorded in `docs/reference/CORE-VERSION-MATRIX.md`.

For AgentFlow itself:
- `GOVERNANCE.md` is the sole normative end-to-end process definition;
- `AI-EXECUTION-RULES.md` is the compact canonical normal-executor rules source;
- `KIT-MANIFEST.md` is the normative shipped inventory;
- README/guides/examples/audit/reference material are non-normative unless explicitly marked;
- secondary documents link to Core rather than restating rules.

Before adding documentation, ask whether a canonical home already exists and whether a reference is sufficient.
