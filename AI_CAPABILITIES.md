# AI Capabilities Catalog

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: AI_PROVIDER_LAYER.md, AGENT_RUNTIME.md, MEMORY_ENGINE.md, RAG_SYSTEM.md, PLUGIN_SDK.md, MCP_SPEC.md, FEATURE_MATRIX.md
Next Expansion: Attach per-capability provider support matrices and API contracts.
Last Updated: 2026-07-23
```

This is the authoritative catalog of every AI capability Dhee_AI supports. Each capability
lists what it is, where it is specified, and its baseline requirements. Capability availability
per provider is normalized by the provider layer
([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)); scheduling/roadmap status lives in
[`FEATURE_MATRIX.md`](FEATURE_MATRIX.md).

## Core generation
- **Chat** — multi-turn conversational generation with system/user/assistant roles and
  message history. Spec: [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md).
- **Structured Output** — schema-constrained responses (JSON schema / typed objects) with
  validation and repair.
- **Embeddings** — vector representations for search and memory. Spec:
  [`RAG_SYSTEM.md`](RAG_SYSTEM.md), [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md).

## Multimodal
- **Vision** — image understanding (describe, analyze, ground).
- **Voice** — speech-to-text and text-to-speech.
- **OCR** — text extraction from images/documents, feeding RAG and structured output.

## Tools & actions
- **Function Calling / Tool Calling** — model-invoked tools with typed schemas; the runtime
  executes and returns results. Spec: [`AGENT_RUNTIME.md`](AGENT_RUNTIME.md),
  [`PLUGIN_SDK.md`](PLUGIN_SDK.md).
- **Browser Automation** — controlled web navigation and extraction as a tool surface.
- **Computer Use** — controlled OS/desktop actions under Human Override with explicit sandboxing
  and confirmation.

## Coding intelligence
- **Code Generation** — produce new code that complies with the specification and standards.
- **Refactoring** — behavior-preserving transformations with tests.
- **Repository Understanding** — index and reason across a whole codebase (structure, symbols,
  dependencies). Spec: [`RAG_SYSTEM.md`](RAG_SYSTEM.md), [`EDITOR_ENGINE.md`](EDITOR_ENGINE.md).

## Reasoning & orchestration
- **Planning** — decompose goals into ordered, verifiable steps.
- **Research** — gather, synthesize, and cite information from multiple sources.
- **Multi-Agent Orchestration** — coordinate specialized agents (manager, planner, backend,
  frontend, etc.) with shared context. Spec: [`AGENT_RUNTIME.md`](AGENT_RUNTIME.md).
- **Autonomous Mode** — long-running, self-directed execution bounded by policy, budgets, and
  Human Override.
- **Team Mode** — collaborative multi-user/multi-agent sessions with shared workspace and memory.

## State & extensibility
- **Memory** — short- and long-term memory across conversation, user, project, workspace, and
  team scopes. Spec: [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md).
- **Workflows** — reusable, composable pipelines and scheduled/event-driven automation. Spec:
  [`WORKFLOW_ENGINE.md`](WORKFLOW_ENGINE.md).
- **Plugins** — third-party capabilities and tools. Spec: [`PLUGIN_SDK.md`](PLUGIN_SDK.md).
- **MCP** — Model Context Protocol client/host compatibility for external tools and resources.
  Spec: [`MCP_SPEC.md`](MCP_SPEC.md).

## Cross-cutting requirements
Every capability must honor: streaming where applicable, token/cost optimization, provider
failover, Human Override for side-effecting actions, structured error handling
([`ERROR_STANDARDS.md`](ERROR_STANDARDS.md)), auditability ([`OBSERVABILITY.md`](OBSERVABILITY.md)),
and the security model ([`SECURITY_MODEL.md`](SECURITY_MODEL.md)).
