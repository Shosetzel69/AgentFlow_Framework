# AgentFlow Compatibility

Status: `REFERENCE`  
Current framework version: `1.3.0`

## 1. Upgrade principle

A framework release never changes a consuming project automatically. Projects explicitly adopt an upgrade through their governance, Project Adapter and config.

Historical artifacts retain the framework/Core semantics under which they were approved. A v1.3 adoption does not retroactively reinterpret an approved v1.2 ATC.

## 2. v1.2.x → v1.3.0

v1.3 retains the document/protocol architecture and adds bounded measurable execution context plus proof/release hardening.

A project adopting v1.3 revalidates at least:

1. `AI-EXECUTION-RULES.md` as the compact canonical normal-executor rules source;
2. Development Analysis `Execution Context` per proposed ATC;
3. authoring-time controlled-context size/readiness;
4. semantic default exclusions and section/range references;
5. durable stage-result / analysis-checkpoint record mapping;
6. explicit evidence sufficiency policy;
7. execution-rules version + controlled-context telemetry in Evidence;
8. external-review durable record/access boundary;
9. candidate composition/equivalence proof;
10. environment-transition readiness;
11. execution-context metric collection where used.

Existing approved v1.2 work does not require bulk rewrite. New/revised v1.3 ATCs use v1.3 templates/rules after explicit project adoption.

## 3. Reference benchmark compatibility

The framework reference execution scenario has its own ID/version. Same-scenario results may be compared across framework releases.

Changing scenario semantics requires a new scenario version and explicit baseline reset recorded in release history. Do not compare different scenario versions as one continuous benchmark.

Initial benchmark: `RES-1 v1.0`, AgentFlow v1.2.0 baseline, durable record in framework work item #12 / ADR-12 lineage.

## 4. Recommended compatibility declaration

For projects adopting v1.3:

`>=1.3.0,<2.0.0`

Projects still on v1.2 remain on their previously validated range until explicit adoption.

## 5. Earlier versions

v1.1.1 was a superseded pre-release candidate. v1.1.0 projects should adopt through documented migration rather than assuming compatibility.

`templates/EXECUTABLE-TASK.md` remains compatibility-only and cannot create execution authority.

## 6. Future major boundary

Machine-readable workflow state, automatic gate/context enforcement, artifact-graph automation, lock/concurrency management and orchestration remain outside v1.3 and require a future architecture/migration decision.
