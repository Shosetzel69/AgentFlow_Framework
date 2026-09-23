# AgentFlow Compatibility

Status: `REFERENCE`  
Current framework version: `1.1.1`

## 1. Upgrade principle

A new AgentFlow Framework release never changes a consuming project automatically.

Each project must explicitly adopt an upgrade through its own Project Adapter and governance.

## 2. v1.1.0 → v1.1.1

v1.1.1 preserves the v1.1 architecture and artifact model, but tightens several process controls.

Before a consuming project declares v1.1.1 active, it should map:

1. `APPROVE_REQUIREMENT <ref>` or an explicitly renamed equivalent;
2. durable approval record system/location;
3. exact candidate identity used by Independent Review;
4. rule that implementation mutation invalidates the old review for promotion;
5. hotfix path that preserves the non-reducible Core controls.

Existing v1.1.0 work items do not need bulk historical rewriting. Apply the new rules prospectively and when active work is next materially touched, unless the consuming project decides otherwise.

## 3. Adapter compatibility

Recommended declaration for projects adopting this release:

`>=1.1.1,<1.2.0`

A v1.1.0 Project Adapter can be upgraded in place by adding the new v1.1.1 fields. Do not overwrite project-specific values with the template.

## 4. Deprecated artifact

`templates/EXECUTABLE-TASK.md` remains available for compatibility but is deprecated.

It may summarize an already approved ATC for a local executor/tool, but it cannot create or modify execution authority.

New projects should use `templates/AGENT-TASK-CONTRACT.md` directly.

## 5. Deferred compatibility impact

Future versions that introduce machine-readable state, artifact graphs, evidence classes, or multi-agent locking may require migration beyond simple documentation/template updates. Those changes are not part of v1.1.1.
