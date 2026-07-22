# API Specification

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, NAMING.md, ERROR_STANDARDS.md
Related Documents: AUTH_SYSTEM.md, AI_PROVIDER_LAYER.md, AGENT_RUNTIME.md, VERSIONING.md
Next Expansion: Publish the OpenAPI document and streaming protocol details for v1 endpoints.
Last Updated: 2026-07-23
```

## Purpose
Define the public, versioned API contract for Dhee_AI (API First). Clients (web, CLI, desktop,
integrations) depend only on this contract.

## Scope
REST endpoints, streaming (SSE/WebSocket), authentication, pagination, error format, rate
limiting, and webhooks.

## Conventions
- Versioned base path: `/v1`. Resource paths use plural, kebab-case nouns; JSON fields and
  query params are `camelCase` (see [`NAMING.md`](NAMING.md)).
- HTTP methods convey intent; actions use sub-resources (`POST /v1/agents/{id}/runs`).
- Errors follow the normalized model in [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md).

## Resource groups (design intent)
- **Auth & identity:** sessions, tokens, users, organizations, teams, API keys
  ([`AUTH_SYSTEM.md`](AUTH_SYSTEM.md)).
- **Chat:** conversations, messages, streaming completions.
- **Agents:** agents, runs, steps, tool invocations ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).
- **Memory & RAG:** memory items, documents, retrieval queries.
- **Workspace:** projects, files, terminal, git operations.
- **Plugins & MCP:** installation, configuration, tool discovery.
- **Admin:** usage, audit logs, settings.

## Streaming
Token streaming for chat and agent runs via SSE (default) and WebSocket (bidirectional), with a
stable event envelope and backpressure handling.

## Pagination, filtering, rate limiting
Cursor-based pagination; consistent filter/sort params; rate limits surfaced via headers and
`RATE_LIMIT.*` errors.

## Versioning & compatibility
Documented endpoints are stable within a MAJOR version per [`VERSIONING.md`](VERSIONING.md);
breaking changes require an ADR and a new version.

## Security
All endpoints authenticated/authorized per [`SECURITY_MODEL.md`](SECURITY_MODEL.md); input
validated at the boundary; no sensitive data in errors or logs.
