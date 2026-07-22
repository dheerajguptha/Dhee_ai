# Technology Stack

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, DECISIONS.md
Related Documents: MONOREPO_STRUCTURE.md, DATABASE_SCHEMA.md, CI_CD.md, DOCKER.md, KUBERNETES.md
Next Expansion: Pin exact versions in a dependency lockfile once implementation begins.
Last Updated: 2026-07-23
```

This document records the chosen technologies and the rationale for each. Changes to the stack
require an ADR in [`DECISIONS.md`](DECISIONS.md). Choices favor openness, type safety, vendor
independence, and long-term maintainability.

## Language & runtime
- **TypeScript (strict)** everywhere — end-to-end type safety (Explicit Over Implicit).
- **Node.js LTS** for backend services and tooling.
- Rationale: one language across client, server, SDKs, and CLI; huge ecosystem; strong tooling.

## Monorepo & build
- **pnpm workspaces** — fast, disk-efficient, strict dependency resolution.
- **Turborepo** — cacheable, parallel task graph.
- Rationale: shared types and coordinated changes with fast builds (ADR-0002).

## Frontend
- **React** with **Vite** — component model and fast dev/build.
- **Monaco Editor** — the editor core (VS Code-class editing).
- **Tailwind CSS** + a headless component library (e.g. Radix primitives) — accessible,
  systematic UI (see [`DESIGN_SYSTEM.md`](DESIGN_SYSTEM.md), [`ACCESSIBILITY.md`](ACCESSIBILITY.md)).
- **TanStack Query** for server state; a light client-state store as needed.

## Backend
- **Node.js** HTTP framework with first-class TypeScript, schema validation, and streaming
  (e.g. Fastify-class). Public contracts in [`API_SPEC.md`](API_SPEC.md).
- **Zod** (or equivalent) for runtime schema validation at all boundaries.
- **WebSocket / Server-Sent Events** for streaming AI responses and live updates.

## AI layer
- Provider-agnostic abstraction ([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)) supporting
  OpenAI, Anthropic, Google AI Studio, Groq, OpenRouter, Ollama (local), Azure OpenAI, Vertex
  AI, and AWS Bedrock.
- Rationale: Zero Vendor Lock-In; local-first option via Ollama.

## Data
- **PostgreSQL** — primary relational store ([`DATABASE_SCHEMA.md`](DATABASE_SCHEMA.md)).
- **pgvector** — embeddings/vector search for memory and RAG.
- **Redis** — cache, rate limiting, ephemeral coordination.
- **Job queue** — background/async work (e.g. Redis- or Postgres-backed).
- **Object storage** — files, artifacts, large blobs (S3-compatible).
- A typed query layer / ORM with migrations (forward-only, reversible where practical).

## Testing & quality
- **Vitest/Jest** (unit/integration), **Playwright** (e2e) — see
  [`TESTING_STRATEGY.md`](TESTING_STRATEGY.md).
- **ESLint** + **Prettier** — linting and formatting; boundary/import rules enforce
  [`ARCHITECTURE.md`](ARCHITECTURE.md).
- **TypeScript** in strict mode as a quality gate.

## Infrastructure & delivery
- **Docker** and **Docker Compose** ([`DOCKER.md`](DOCKER.md)), **Kubernetes**-ready
  ([`KUBERNETES.md`](KUBERNETES.md)).
- **GitHub Actions** for CI/CD ([`CI_CD.md`](CI_CD.md)).
- **OpenTelemetry** for tracing/metrics/logs ([`OBSERVABILITY.md`](OBSERVABILITY.md)).

## Principles applied
Every choice above is portable and swappable to honor Zero Vendor Lock-In. Where a managed
service is convenient, an open, self-hostable alternative must remain viable.
