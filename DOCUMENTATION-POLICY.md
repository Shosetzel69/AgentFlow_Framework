# AgentFlow Documentation Policy

Status: `REFERENCE CORE`
Version: `1.1.1`

## 1. Goal

Documentation must reduce execution risk without becoming execution overhead.

Core rule:

> Read and maintain only the context required for the current task.

## 2. Documentation layers

### L0 — Entry / Handoff

Examples:

- issue;
- task;
- PR/MR description;
- release handoff.

Purpose: explain what is being done and where authoritative detail lives.

Rule: short, decision-oriented, links instead of copied history.

### L1 — Canonical Current State

Examples:

- Architecture;
- Governance;
- Requirements;
- Data/API contracts;
- Delivery lifecycle.

Purpose: current approved state.

Rule: read only relevant sections.

### L2 — Operational Procedures

Examples:

- runbooks;
- migration/cutover procedures;
- QA procedures.

Purpose: safely execute one procedure.

Rule: one purpose per document; do not duplicate architecture/history.

### L3 — Reference / History

Examples:

- analysis documents;
- reports;
- superseded material;
- archived runbooks.

Purpose: preserve reasoning/evidence.

Rule: never load by default.

## 3. Progressive context loading

Default execution context:

1. current task/issue;
2. AI execution rules;
3. affected code/configuration;
4. only relevant canonical sections.

Do not automatically load the entire repository documentation set.

If more than five supporting documents appear necessary, create a short Context Map before loading more material.

## 4. Context Map

A task may declare:

```text
Required context:
- exact files/sections

Optional context:
- only if a named question remains

Excluded context:
- historical/superseded material that must not drive execution
```

The handoff should be executable without reconstructing prior chat history.

## 5. Current-state vs history

Analysis documents are decision-support history, not a second current-state manual.

After a decision:

- keep the decision outcome/reference;
- update canonical current-state documentation;
- do not continuously synchronize historical analysis with later implementation details.

## 6. Update discipline

Update only documentation materially affected by a change.

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

For canonical operational documents, keep the current version at one stable path and use version-control history for old versions.

Recommended metadata:

```text
Status: CANONICAL | WORKING | HISTORICAL | SUPERSEDED
Version: vX.Y.Z
Applicability: CURRENT | HISTORICAL_ONLY
Applies to: AGENTFLOW | LEGACY-ADAPTED | BOTH
Effective from: YYYY-MM-DD
Supersedes: <optional>
```

Do not create active `-v1`, `-v2`, `-final` copies only for version history.

## 8. Documentation safeguard

Before adding a document, ask:

1. Is this needed to execute, decide, or operate?
2. Does it already have a canonical home?
3. Can I link instead of duplicate?
4. Will an agent know exactly what to read?
5. Am I preserving history instead of mixing it with current state?

If a canonical home already exists, update or link it instead of creating another source of truth.

## 9. Framework self-consistency

For AgentFlow itself:

- `GOVERNANCE.md` is the only normative end-to-end process definition;
- `KIT-MANIFEST.md` is the only normative shipped-file inventory;
- README, adoption guides, translations, examples, and audit/reference material are non-normative unless explicitly marked otherwise;
- convenience documents should link to Core instead of restating process rules;
- version changes must update `VERSION`, `CHANGELOG.md`, and compatibility guidance where consumer action is required.
