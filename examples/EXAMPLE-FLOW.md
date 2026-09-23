# Example AgentFlow Execution

Status: `NON-NORMATIVE EXAMPLE`  
Framework compatibility: `1.1.1`

This example illustrates one possible execution. The normative process, statuses, and approvals are defined only in `GOVERNANCE.md`.

Scenario: add export-to-CSV to an existing application.

## 1. Requirement

The Requirement defines:

- users can export the currently filtered table;
- CSV only;
- no scheduled export;
- no email delivery;
- export must respect existing authorization.

The owner records the required Requirement Approval in the project's durable approval record.

## 2. Development Analysis

Baseline inspection finds:

- existing table API already returns all required fields;
- no new persistence;
- no new auth boundary;
- no shared API contract change required.

Architecture Delta Check: no Architecture Gate required.

Development Analysis proposes one ATC.

## 3. ATC

```text
ATC-CSV-01
Objective: add authorized CSV export of current filtered table.
Scope: UI button + server export endpoint + tests.
Out of scope: scheduled exports, XLSX, email.
Retry limit: 2.
```

The exact ATC approval is recorded durably before implementation.

## 4. Implementation and evidence

Executor implements only the contract and produces an Evidence Bundle for candidate `abc123...`.

## 5. Independent Review

Independent reviewer checks candidate `abc123...` against the ATC and its Evidence Bundle.

The verdict is recorded for that exact candidate identity.

If implementation changes, the review must be repeated for the new identity.

## 6. DEV / TEST / PROD

Release promotion follows `DELIVERY-LIFECYCLE.md` for the exact reviewed candidate.

The example intentionally does not restate the release gates here.
