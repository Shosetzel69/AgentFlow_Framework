# AgentFlow — Market Landscape

Status: `RESEARCH SNAPSHOT`
Verified: `2026-09-23`

This is not a product endorsement or legal/commercial assessment. It is a current comparison intended to guide AgentFlow design and avoid rebuilding capabilities already available elsewhere.

## 1. Closest references

### GitHub Spec Kit

Current positioning: open-source toolkit for Spec-Driven Development and other structured processes for coding agents.

Relevant capabilities observed:

- specification / planning / tasks / implementation workflows;
- workflows that chain commands, prompts, shell steps and human checkpoints;
- conditional logic, loops and fan-out/fan-in;
- persisted workflow state with pause/resume;
- extensions, presets, bundles and multiple agent integrations;
- support for existing projects.

License: MIT.

Why it matters to AgentFlow:

Spec Kit now overlaps strongly with the workflow/state and conversation-continuity problem. AgentFlow should not build a generic workflow engine without first evaluating whether Spec Kit can act as an execution substrate.

Official sources:

- https://github.github.com/spec-kit/
- https://github.com/github/spec-kit
- https://github.com/github/spec-kit/blob/main/docs/reference/workflows.md

### BMad Method

Current positioning: a free AI-assisted software-development methodology/toolset spanning thinking/planning and build activities.

Relevant capabilities observed:

- structured analysis/planning/build workflows;
- named skills/roles;
- support for existing codebases;
- separation of thinking work and implementation work;
- human decision-making remains part of the process.

License: MIT. Official repository states BMad is free.

Why it matters to AgentFlow:

BMad is a strong reference for role separation, handoffs and staged AI-assisted development. AgentFlow's distinction must be stronger than "multiple specialized AI roles".

Official sources:

- https://github.com/bmad-code-org/BMAD-METHOD
- https://github.com/bmad-code-org/BMAD-METHOD/blob/main/docs/index.md

### Kiro

Current positioning: AI development environment with specs and structured agentic development features.

Commercial model observed:

- perpetual Free tier;
- current Free tier includes 50 credits, subject to model/rate limits;
- paid tiers exist for greater capacity.

Why it matters to AgentFlow:

Useful product/UX benchmark, but not a desirable hard dependency for a tool-neutral, low-cost Core.

Official source:

- https://kiro.dev/pricing/

### GitLab Duo Agent Platform

Current positioning: platform-integrated agents/flows and AI governance.

Relevant capability observed:

- tool governance at the execution boundary;
- tool actions can be allowed, require human approval, or be denied;
- governance applies based on configured rules;
- agent platform availability uses GitLab Credits; some governance capabilities are tier-dependent/beta.

Why it matters to AgentFlow:

GitLab demonstrates the kind of machine enforcement AgentFlow currently lacks. It is best treated as an enforcement benchmark, not as a tool-neutral Core dependency.

Official sources:

- https://docs.gitlab.com/user/ai-governance/tool-governance/
- https://docs.gitlab.com/user/duo_agent_platform/
- https://docs.gitlab.com/user/duo_agent_platform/turn_on_off/

## 2. Current competitive interpretation

AgentFlow should not claim novelty for:

- "specification before coding";
- structured AI development;
- role-based AI workflows;
- human checkpoints;
- resumable workflows.

Those capabilities exist elsewhere.

The current differentiation hypothesis is the integrated control model:

```text
Requirement authority
        ↓
Architecture authority
        ↓
Development Analysis
        ↓
bounded Agent Task Contract
        ↓
explicit scoped authorization
        ↓
Implementation
        ↓
Evidence Bundle
        ↓
Independent Review
        ↓
immutable release candidate
        ↓
independent TEST
        ↓
human PROD authorization
```

Combined with the Conversation Independence Principle, the aim is:

> controlled continuity across independent AI sessions, not merely agent orchestration.

## 3. Free / low-cost relevance

For a zero-license-cost investigation:

- GitHub Spec Kit: strong candidate; MIT;
- BMad Method: strong candidate; MIT/free;
- Kiro: free tier, but capacity-limited and vendor service;
- GitLab Duo Agent Platform: not a zero-cost equivalent for the relevant platform/governance usage; credits/tier constraints apply.

## 4. Design implication

Before AgentFlow adds a v2 orchestration engine, perform a capability-level gap analysis against Spec Kit and BMad.

Potential strategic options:

1. build a standalone AgentFlow engine;
2. integrate AgentFlow governance over Spec Kit workflows;
3. reuse selected BMad role/handoff concepts while preserving AgentFlow authority/evidence/release rules;
4. remain documentation/protocol-first and add only lightweight machine validation.

No option is approved yet.
