# AgentFlow Documentation Policy

Status: `REFERENCE CORE`  
Document version: `1.2.0`  
Framework compatibility: `1.2.x`

## 1. Goal

Documentation must reduce execution risk without becoming execution overhead.

Core rule:

> Read and maintain only the context required for the current task.

## 2. Documentation layers

### L0 — Entry / Handoff

Issues/work items, PR/MR/change descriptions, release handoffs.

Purpose: explain what is being done and where authoritative detail lives.

### L1 — Canonical Current State

Examples:

- Governance;
- Architecture;
- Requirements;
- Data/API contracts;
- AgentFlow operating/release rules;
- Project Adapter/config.

Purpose: current approved state.

### L2 — Operational Procedures

Runbooks, migration/cutover, QA/test procedures.

### L3 — Reference / History

Analyses, reports, superseded material, audits, archived runbooks.

History is never loaded as current truth by default.

## 3. Progressive context loading

Default execution context:

1. current task/work item;
2. AI execution rules;
3. affected code/configuration;
4. only relevant canonical sections.

If more than five supporting documents appear necessary, create a short Context Map before loading more material.

## 4. Context Map

```text
Required context:
- exact files/sections

Optional context:
- only if a named question remains

Excluded context:
- historical/superseded material that must not drive execution
```

The handoff should be executable without reconstructing prior chat history.

## 5. Current state vs history

After a decision:

- keep the decision outcome/reference;
- update canonical current-state documentation;
- preserve analysis/history separately;
- do not make historical analysis a second current-state manual.

## 6. Update discipline

Prefer:

- one canonical source;
- links from secondary places;
- archive/supersede obsolete material.

Avoid:

- copy/paste synchronization;
- multiple current sources of truth;
- documentation-only churn;
- documents created only to satisfy process.

## 7. Versioning

Canonical documents keep one stable path and use version-control history for old versions.

Recommended metadata:

```text
Status: CANONICAL | WORKING | HISTORICAL | SUPERSEDED
Document version: X.Y.Z
Framework compatibility: <range>
Applicability: CURRENT | HISTORICAL_ONLY
```

Templates use:

```text
Template status:
Template version:
Framework compatibility:
```

The shipped versions are recorded in `docs/reference/CORE-VERSION-MATRIX.md`.

## 8. Artifact identity

Stable AgentFlow artifact identity and mandatory parent links are defined in `ARTIFACT-TRACEABILITY.md`.

Document lifecycle metadata is separate from work-item workflow Phase/Status.

## 9. Framework self-consistency

For AgentFlow itself:

- `GOVERNANCE.md` is the only normative end-to-end process definition;
- `KIT-MANIFEST.md` is the only normative shipped-file inventory;
- `docs/reference/CORE-VERSION-MATRIX.md` is the shipped artifact-version mapping;
- README, adoption guides, translations, examples, audit/reference material are non-normative unless explicitly marked otherwise;
- convenience documents should link to Core instead of restating process rules;
- release version changes update `VERSION`, `CHANGELOG.md`, compatibility guidance, manifest, and version matrix.

## 10. Documentation safeguard

Before adding a document, ask:

1. Is this needed to execute, decide, operate, audit, or version?
2. Does it already have a canonical home?
3. Can I link instead of duplicate?
4. Will an agent know exactly what to read?
5. Am I preserving history instead of mixing it with current state?

If a canonical home already exists, update or link it instead of creating another source of truth.
