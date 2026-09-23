# AgentFlow Changelog

## 1.1.1 — Audit remediation

Type: patch-level framework correctness/consistency release.

Source: independent documentation audit `AF-AUDIT-2026-09-23-01`.

### Fixed

- **F-02** — added `APPROVE_REQUIREMENT <ref>` to the canonical approval model, configuration, and Requirement template.
- **F-03** — Independent Review verdicts are now bound to one exact candidate identity; implementation mutation invalidates the prior verdict for promotion.
- **F-05** — defined minimum non-reducible hotfix controls; urgency may reduce test breadth but not approval/evidence/review/identity/recovery/PROD authorization controls.
- **F-08** — `GOVERNANCE.md` is now the single normative end-to-end process definition.
- **F-09** — added instruction-provenance rules for untrusted content encountered by AI agents.
- **F-10** — approvals must be recorded in a project-configured durable approval record before workflow transition.
- **F-12** — aligned framework/Core versioning and added changelog plus compatibility guidance.
- **F-13** — Architecture Decision template now uses the canonical Architecture phase/status vocabulary.
- **F-16** — `EXECUTABLE-TASK.md` is explicitly deprecated and cannot replace an approved ATC.
- **F-25** — Romanian usage guide is now non-normative adoption/use guidance with links to Core.
- **F-27** — `KIT-MANIFEST.md` is now the canonical shipped-file inventory; README no longer maintains a competing tree.

### Deliberately deferred

The following audit items are not implemented in 1.1.1:

- evidence integrity classes;
- candidate composition manifest;
- graded review independence;
- machine-readable state/gate enforcement;
- artifact graph;
- cross-cycle budget;
- multi-agent identity/locking/concurrency;
- post-release observation/operations model;
- forward-fix authorization;
- security/operations/compliance adapters;
- canonical delivery metrics.

See Issue #5 for the release scope.

## 1.1.0 — Independent kit baseline

Initial standalone AgentFlow Framework extraction, bootstrap procedure, Core documents, templates, audit structure, and context handoff.
