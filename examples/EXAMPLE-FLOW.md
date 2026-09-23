# Example AgentFlow Execution

Status: `NON-NORMATIVE EXAMPLE`  
Framework compatibility: `1.2.x`

This example illustrates one possible execution. The normative process, statuses, and approvals are defined only in Core documents.

Scenario: add export-to-CSV to an existing application.

## 1. Requirement

Create `REQ-42` with scope and acceptance criteria.

Owner durably records:

`APPROVE_REQUIREMENT REQ-42`

## 2. Development Analysis

Create `DA-42-01`.

Baseline inspection finds no Architecture Gate trigger and proposes `ATC-42-01`.

## 3. ATC

The ATC declares:

- scope/out-of-scope;
- mandatory tests;
- minimum evidence class;
- retry limit;
- remediation-cycle budget;
- execution owner/provenance fields.

Owner durably records:

`APPROVE_TASK_CONTRACT ATC-42-01`

## 4. Implementation / evidence

Executor produces candidate `abc123...` and `EV-ATC-42-01-01`.

Mandatory checks reference CI/test artifacts rather than executor assertions.

## 5. Independent Review

Reviewer satisfies the configured independence level and records `REV-ATC-42-01-01` for exact candidate `abc123...`.

If implementation changes, that review no longer applies to the new candidate.

## 6. Candidate Manifest

DEV verification passes.

Create `CM-abc123` linking REQ/DA/ATC/EV/REV for all included work.

The exact candidate is frozen.

## 7. TEST / PROD

TEST validates the exact frozen candidate.

Release promotion then follows `DELIVERY-LIFECYCLE.md`.

The release record traces the production candidate back through the Candidate Manifest.

This example intentionally does not restate the full lifecycle gates.
