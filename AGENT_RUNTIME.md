# Agent Runtime

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, AI_PROVIDER_LAYER.md, AI_CAPABILITIES.md
Related Documents: MEMORY_ENGINE.md, RAG_SYSTEM.md, WORKFLOW_ENGINE.md, PLUGIN_SDK.md, SECURITY_MODEL.md
Next Expansion: Define the agent lifecycle, message protocol, and orchestration policies.
Last Updated: 2026-07-23
```

## Purpose
Define the multi-agent execution runtime: how agents plan, call tools, collaborate, and execute
work under human oversight.

## Scope
Agent lifecycle, planning, tool calling, multi-agent orchestration, state, autonomy bounds, and
Human Override.

## Built-in agents (design intent)
Manager, Planner, Architect, Backend, Frontend, Database, DevOps, Security, Testing,
Documentation, Research, Browser, Computer, Deployment, Review. Users can define custom agents
via the Agent/Plugin SDK ([`PLUGIN_SDK.md`](PLUGIN_SDK.md)).

## Execution model
- **Planning:** decompose goals into ordered, verifiable steps (Planner/Manager).
- **Tool calling:** typed tool schemas; the runtime executes tools and returns results.
- **Orchestration:** the Manager coordinates specialized agents with shared context/memory.
- **Verification:** steps are checked against the specification before completion.

## Human Override
Side-effecting or irreversible actions require confirmation; all actions are visible and
auditable ([`OBSERVABILITY.md`](OBSERVABILITY.md)). Autonomy is bounded by policy and budgets.

## State & memory
Agents read/write memory across scopes ([`MEMORY_ENGINE.md`](MEMORY_ENGINE.md)) and retrieve
context via RAG ([`RAG_SYSTEM.md`](RAG_SYSTEM.md)).

## Safety & security
Tools and computer/browser use run sandboxed with least privilege
([`SECURITY_MODEL.md`](SECURITY_MODEL.md)); errors normalized per
[`ERROR_STANDARDS.md`](ERROR_STANDARDS.md).
