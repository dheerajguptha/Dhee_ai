# AI Provider Layer

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, AI_CAPABILITIES.md, PRINCIPLES.md
Related Documents: AGENT_RUNTIME.md, ERROR_STANDARDS.md, MEMORY_ENGINE.md, RAG_SYSTEM.md
Next Expansion: Define the provider interface, capability model, and routing policy in detail.
Last Updated: 2026-07-23
```

## Purpose
Provide a unified, provider-agnostic abstraction over many AI model vendors and local models, so
the rest of the system never depends on a specific vendor (Zero Vendor Lock-In).

## Scope
Chat, streaming, tool/function calling, embeddings, structured output, vision, voice, model
metadata, routing, failover, token optimization, and cost accounting.

## Supported providers (design intent)
OpenAI, Anthropic, Google AI Studio, Groq, OpenRouter, Ollama (local), Azure OpenAI, Vertex AI,
AWS Bedrock. New providers are added via the Provider SDK ([`PLUGIN_SDK.md`](PLUGIN_SDK.md)).

## Capability model
Each provider/model declares capabilities (context window, tools, vision, voice, structured
output, embeddings). The layer normalizes differences and degrades gracefully when a capability
is absent (see [`AI_CAPABILITIES.md`](AI_CAPABILITIES.md)).

## Core components
- **Provider interface:** a single typed contract all adapters implement.
- **Router & smart model selection:** choose provider/model by capability, cost, latency, and
  policy.
- **Failover:** switch providers on `PROVIDER.*` errors ([`ERROR_STANDARDS.md`](ERROR_STANDARDS.md)).
- **Context manager & token optimizer:** assemble and compress context within budgets.
- **Prompt compiler:** structured, reusable prompt construction.
- **Streaming engine:** uniform streaming envelope across providers.

## Reliability & cost
Retries with backoff and circuit breaking; per-request and per-tenant cost/token accounting;
caching where safe.

## Security
API keys are secrets ([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)); prompts and completions
containing sensitive data are never logged in the clear.
