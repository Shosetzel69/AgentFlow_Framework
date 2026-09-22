# AgentFlow Adoption Guide

> For a project-specific guided adoption, run `BOOTSTRAP-PROCEDURE.md` first. It produces the proposed Project Adapter, configuration, gap map and adoption verdict.

## 1. Greenfield project

Recommended sequence:

1. copy this kit into the repository or project handbook;
2. complete `FRAMEWORK-CONFIG.md`;
3. create the project adapter from `templates/PROJECT-ADAPTER.md`;
4. choose canonical locations for Architecture, Requirements, and API/Data contracts;
5. configure branch protection and CI/CD;
6. adopt the work-item header and status taxonomy;
7. start all new work with AgentFlow.

## 2. Existing project

Do not retrofit every old issue and document at once.

Recommended transition:

```text
new work → AGENTFLOW
materially-started old work → LEGACY-ADAPTED
```

Use one release lifecycle for both.

When the final legacy work item is closed, retire the transition mode.

## 3. Lightweight mode

For a solo or small project, do not add unnecessary enterprise controls.

Minimum recommended gates:

- Requirement Approval;
- Architecture Gate only when triggered;
- Task Contract Approval;
- Independent Review;
- TEST Pass;
- PROD GO.

Do not add CAB, multi-person approval, release trains, or formal risk scoring unless justified.

## 4. Team mode

For teams, map logical roles to real people/groups:

- Product Owner;
- Architect;
- Development Analyst;
- Executor;
- Reviewer;
- QA;
- Release Approver.

The same person may hold multiple roles if risk policy allows, but review/test independence should remain meaningful.

## 5. AI-heavy mode

If AI agents execute most work, strengthen:

- stable task references;
- exact candidate identity;
- explicit approval tokens;
- stop conditions;
- evidence mapping;
- context limits;
- branch/environment protections.

Do not compensate for uncertain AI behavior by loading the entire project history. Improve contracts and canonical documentation instead.

## 6. First implementation checklist

Before the first AgentFlow task, verify:

- owner/approver identified;
- project adapter exists;
- default branch protected;
- DEV/TEST/PROD mapping defined;
- candidate identity defined;
- task approval token defined;
- PROD approval token defined;
- rollback policy defined;
- required evidence defined;
- independent review executor identified;
- canonical architecture and requirements locations defined.
