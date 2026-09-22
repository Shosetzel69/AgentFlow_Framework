# AgentFlow — Origin and Design Intent

Status: `WORKING DESIGN RECORD`
Date: `2026-09-23`

## 1. Origin

AgentFlow did not start from the goal of creating another coding-agent framework.

It emerged from a practical problem encountered while developing a real software project through multiple AI chats and roles:

- work was split across Architecture, Development, Review, QA and release conversations;
- important decisions existed in different chats;
- after interruptions it was not always obvious where the project actually was;
- generic instructions such as "continue" could be interpreted too broadly;
- conversation history was becoming an unreliable place to keep project state.

The original problem can be stated as:

> How can software delivery remain deterministic and recoverable when work is fragmented across multiple AI conversations, agents and sessions?

## 2. Core design problem

Chat is a useful workspace, but a poor project-state manager.

AgentFlow therefore separates:

```text
CHAT / SESSION
= transient workspace

PROJECT STATE
= persistent artifacts
+ explicit phase/status
+ explicit authorization
+ evidence
```

The framework must not require reconstruction of the project from conversation history.

## 3. Primary outcomes

AgentFlow is intended to provide three properties.

### Continuity

Changing chat, agent, model or session must not cause loss of execution state.

### Authority

At any moment it must be clear:

- what is approved;
- what is not approved;
- which role owns the current decision;
- what the current executor is allowed to do.

### Traceability

A new participant must be able to reconstruct:

- the requirement;
- relevant architecture decisions;
- authorized execution contract;
- exact implementation candidate;
- evidence;
- review/test/release state.

## 4. Conversation Independence Principle

> No information required for controlled continuation of the project should exist exclusively in a conversation.

Conversation history, AI memory and local scratchpads are context, not canonical project state.

Material decisions, approvals, blockers, contracts and evidence must be persisted in project artifacts.

## 5. Cold Start Test

A project using AgentFlow should pass this test:

> An agent with no access to previous conversations can identify the current state, authority, next action and required context using only project artifacts.

The agent must be able to answer:

1. What are we trying to achieve?
2. What has already been decided?
3. What phase and status are current?
4. What is approved and what is not?
5. What blocks progress?
6. Which role acts next?
7. What exact artifact/candidate is current?
8. What evidence exists?

If those answers require searching old chat history, continuity is incomplete.

## 6. Continuation Record — design candidate

A lightweight continuation artifact is a candidate addition to a future Core version:

```text
Current State:
Last Completed Gate:
Current Authority:
Current Artifact:
Blocked By:
Next Action:
Next Owner / Role:
Required Context:
```

This is not intended to be a chat summary or chronological log. It is the minimum state required for correct resumption.

## 7. Why the existing Core controls exist

The current controls can be understood as mechanisms supporting continuity, authority and traceability:

- Phase / Status taxonomy → current state;
- explicit approval tokens → authority;
- Architecture Gate → decision ownership;
- ATC → bounded execution;
- retry limits / stop conditions → fail-closed execution;
- Evidence Bundle → persistent proof;
- Independent Review → independent validation;
- immutable candidate → identity continuity across environments;
- Release Record → production traceability;
- progressive context loading → bounded resumption context.

## 8. Positioning

AgentFlow should not primarily position itself as:

- another AI coding tool;
- another multi-agent runtime;
- another spec generator.

A more accurate working definition is:

> AgentFlow is a continuity and control layer for software delivery performed through AI agents and independent conversational sessions.

A broader description remains valid:

> governance + SDLC protocol for agent-assisted software delivery.

## 9. Design guardrail

Future evolution should preserve the original problem.

A new feature belongs in Core only when it materially improves one or more of:

- continuity;
- authority;
- traceability;
- execution safety;
- evidence-based promotion.

Features specific to a source-control platform, cloud, AI vendor or organization belong in adapters unless they are necessary to the generic control model.
