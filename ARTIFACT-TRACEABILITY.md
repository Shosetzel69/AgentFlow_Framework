# AgentFlow Artifact Identity and Traceability

Status: `REFERENCE CORE`  
Document version: `1.0.0`  
Framework compatibility: `1.2.x`

## 1. Purpose

AgentFlow requires stable artifact identity so a new agent/reviewer can reconstruct the chain from approved intent to production without searching conversation history.

This document defines a **static/manual traceability model**. Automated artifact graphs and dependency verification are deferred to the future executable framework architecture.

## 2. Canonical artifact types

Recommended typed IDs:

| Artifact | ID pattern |
|---|---|
| Requirement | `REQ-<n>` |
| Architecture Decision | `ADR-<n>` |
| Development Analysis | `DA-<req>-<seq>` |
| Agent Task Contract | `ATC-<req>-<seq>` |
| Evidence Bundle | `EV-<atc>-<seq>` |
| Independent Review | `REV-<atc>-<seq>` |
| Candidate Manifest | `CM-<candidate-ref>` |
| Release Record | `REL-<n>` |

A project may map these to native tracker IDs if its Project Adapter defines an equivalent stable typed-ID scheme.

Requirements:

- IDs are unique within the project namespace;
- IDs do not change when artifact content is amended;
- superseded artifacts keep their IDs and point to their successor;
- candidate identity remains separate from artifact ID.

## 3. Mandatory parent links

### Requirement

Root artifact. May link to parent business initiative, but AgentFlow does not require one.

### Architecture Decision

Must link to:

- triggering Requirement(s) or architecture question/work item.

### Development Analysis

Must link to:

- approved Requirement;
- relevant approved ADR(s), if any.

### Agent Task Contract

Must link to:

- parent Development Analysis;
- parent Requirement;
- relevant ADR(s), if any.

### Evidence Bundle

Must link to:

- exact ATC;
- exact candidate identity.

### Independent Review

Must link to:

- exact ATC;
- Evidence Bundle;
- exact reviewed candidate identity.

### Candidate Manifest

Must link to:

- exact candidate identity;
- every included ATC;
- Evidence Bundle and Independent Review for every included ATC;
- relevant Requirement/ADR/DA references, directly or resolvably through ATCs.

### Release Record

Must link to:

- Candidate Manifest;
- exact promoted candidate;
- PROD_GO approval record;
- deployment/smoke evidence.

## 4. Traceability completeness rule

A release is traceability-complete when each included candidate change can be resolved through:

```text
REL
→ CM
→ ATC
→ DA
→ REQ
→ ADR(s), where applicable
```

and verification can be resolved through:

```text
ATC
→ EV
→ REV
→ exact candidate
```

No automated graph inference is claimed in v1.2.

## 5. Native-system mappings

A Project Adapter may map AgentFlow IDs to GitHub Issues, GitLab Issues, Jira keys, Azure Boards IDs, signed records, or another durable system.

The native ID may serve as the numeric/string component, but the artifact type and stable parent links must remain unambiguous.

## 6. Supersession

When an artifact is superseded:

- preserve the prior artifact;
- mark its document lifecycle as `SUPERSEDED`;
- record `Superseded by: <new-id>`;
- do not reuse the old ID for new semantics.

Work-item workflow status and document lifecycle remain separate.
