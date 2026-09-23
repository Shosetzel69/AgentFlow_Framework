# AgentFlow Compatibility

Status: `REFERENCE`  
Current framework version: `1.2.0`

## 1. Upgrade principle

A framework release never changes a consuming project automatically.

Each project explicitly adopts an upgrade through its own governance, Project Adapter, and config.

## 2. v1.1.0 → v1.2.0

v1.2.0 retains the v1 process architecture but strengthens its contracts and traceability.

A consuming project adopting v1.2 must add/map:

1. bootstrap and Requirement approval tokens;
2. durable approval record;
3. typed artifact IDs / parent links;
4. Development Analysis artifact;
5. evidence classes and mandatory-check proof strength;
6. review independence level;
7. candidate-bound review;
8. Candidate Manifest;
9. remediation-cycle budget;
10. executor provenance/handoff;
11. phase-scoped access boundary;
12. production-data non-PROD rule;
13. forward-fix recovery path;
14. revalidation metadata/gap ownership;
15. updated machine-readable config schema.

Existing historical items do not need bulk rewriting. Apply v1.2 rules prospectively and to active work when materially touched, unless the consuming project chooses a stricter migration.

## 3. Recommended compatibility declaration

`>=1.2.0,<2.0.0`

This communicates compatibility with the protocol/document architecture before the future executable framework major version.

## 4. v1.1.1 status

v1.1.1 was a pre-release audit-remediation candidate and was superseded before merge/release.

Projects should upgrade from v1.1.0 directly to v1.2.0.

## 5. Deprecated artifact

`templates/EXECUTABLE-TASK.md` remains compatibility-only and cannot create execution authority.

## 6. Future major compatibility

Machine-readable workflow state, automated policy checks, artifact-graph automation, lock/concurrency management, and an orchestrator will require a major-version architecture/migration decision.

They are not part of v1.2.0.
