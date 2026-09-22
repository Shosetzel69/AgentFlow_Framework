# Example AgentFlow Execution

Scenario: add export-to-CSV to an existing application.

## 1. Requirement

Business requirement is approved:

- users can export the currently filtered table;
- CSV only;
- no scheduled export;
- no email delivery;
- export must respect existing authorization.

## 2. Development Analysis

Baseline inspection finds:

- existing table API already returns all required fields;
- no new persistence;
- no new auth boundary;
- no shared API contract change required.

Architecture Delta Check: **no Architecture Gate required**.

Development Analysis proposes one ATC.

## 3. ATC

```text
ATC-CSV-01
Objective: add authorized CSV export of current filtered table.
Scope: UI button + server export endpoint + tests.
Out of scope: scheduled exports, XLSX, email.
Retry limit: 2.
```

Owner issues:

```text
APPROVE_TASK_CONTRACT ATC-CSV-01
```

## 4. Implementation

Executor implements only the contract and produces evidence:

- files changed;
- unit tests;
- authorization test;
- CSV escaping test;
- build result;
- no new dependencies.

## 5. Review

Independent reviewer checks exact candidate against ATC and Evidence Bundle.

Verdict:

```text
REVIEW_PASS
```

## 6. DEV and candidate freeze

DEV verification passes.

```text
CANDIDATE_ID = abc123...
```

Candidate is frozen.

## 7. TEST

TEST validates the exact candidate:

- export works;
- filters respected;
- unauthorized request rejected;
- CSV opens correctly.

Verdict:

```text
TEST_PASS
```

## 8. Production gate

Rollback is previous known-good deployment.

Owner issues:

```text
PROD_GO abc123...
```

Exact candidate is deployed.

Smoke passes.

Final status:

```text
DONE
```
