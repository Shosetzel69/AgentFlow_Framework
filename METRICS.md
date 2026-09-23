# AgentFlow Metrics Catalogue

Status: `REFERENCE CORE`  
Document version: `1.0.0`  
Framework compatibility: `1.2.x`

## 1. Purpose

This catalogue defines a minimal common metric vocabulary so projects can evaluate AgentFlow delivery without introducing a metrics engine.

v1.2 defines **what** may be measured. Automated collection from machine-readable state is deferred to the future executable framework.

## 2. Canonical metrics

| Metric | Definition |
|---|---|
| Requirement-to-PROD lead time | elapsed time from durable Requirement Approval to successful PROD smoke/closure |
| ATC cycle time | elapsed time from durable ATC approval to implementation/evidence ready |
| First-pass review success | percentage of reviewed candidates receiving REVIEW_PASS without remediation |
| Remediation cycles per ATC | count of returns to implementation after REVIEW_FAIL or TEST_FAIL |
| Architecture escalation frequency | count/rate of work items returning to Architecture Gate |
| TEST failure rate | percentage of candidate TEST executions resulting in TEST_FAIL |
| Rollback rate | percentage of production releases requiring rollback |
| Forward-fix rate | percentage of production failures using the explicit forward-fix exception |
| Blocked time by phase | elapsed time work remains in a phase-specific BLOCKED status |
| Approval wait time | elapsed time between *_READY_FOR_APPROVAL / gate-ready state and durable approval |

Projects may add metrics but should not redefine these names with different meanings.

## 3. Collection

In v1.2 metrics may be collected manually or through project-specific tooling.

Do not claim framework-level automated metrics unless the project actually implements them.

## 4. Gate response expectations

A Project Adapter may define optional response expectations for gates, for example:

- Requirement Approval: target response within N business days;
- Architecture Approval: target response within N business days;
- ATC Approval: target response within N business days;
- Independent Review: target response within N business days;
- PROD GO: target response within N hours/days.

These are service expectations, not implicit approvals. Expiry never grants authority automatically.

If an expectation is missed, surface the blocked/waiting item; do not auto-transition it.

## 5. Future automation boundary

Canonical metrics derived automatically from machine-readable state transitions belong to the future executable AgentFlow architecture and are intentionally out of scope for v1.2.
