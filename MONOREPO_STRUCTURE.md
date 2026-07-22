# Monorepo Structure

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, TECH_STACK.md, NAMING.md
Related Documents: DECISIONS.md, CI_CD.md, PLUGIN_SDK.md
Next Expansion: Add the concrete workspace config and import-boundary lint rules when code lands.
Last Updated: 2026-07-23
```

Dhee_AI is a single TypeScript monorepo (ADR-0002) managed with pnpm workspaces and Turborepo.
This document defines the layout, boundaries, and rules. Naming follows [`NAMING.md`](NAMING.md).

## Top-level layout

```
Dhee_ai/
  apps/            # deployable applications
  packages/        # shared libraries and SDKs
  milestones/      # milestone specifications
  <spec docs>.md   # the Engineering Constitution and specifications
  .github/         # CI templates
  .cursor/         # Cursor rules
```

## Applications (`apps/*`)
- `apps/web` — React + Monaco web IDE (primary client).
- `apps/api` — Node backend: gateway, auth, and core services host.
- `apps/cli` — the `dhee` CLI.
- `apps/desktop` — desktop shell wrapping the web app (later phase).
- `apps/docs` — documentation site (optional).

Apps are **composition roots**: they wire packages together but contain minimal business logic.

## Packages (`packages/*`)
- `@dhee/core` — shared domain types, contracts, and utilities.
- `@dhee/config` — typed configuration and environment validation.
- `@dhee/ai-provider` — provider abstraction ([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)).
- `@dhee/agent-runtime` — agent orchestration ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).
- `@dhee/memory` — memory engine ([`MEMORY_ENGINE.md`](MEMORY_ENGINE.md)).
- `@dhee/rag` — retrieval-augmented generation ([`RAG_SYSTEM.md`](RAG_SYSTEM.md)).
- `@dhee/workflow` — workflow engine ([`WORKFLOW_ENGINE.md`](WORKFLOW_ENGINE.md)).
- `@dhee/plugin-sdk`, `@dhee/provider-sdk`, `@dhee/tool-sdk` — extensibility SDKs
  ([`PLUGIN_SDK.md`](PLUGIN_SDK.md)).
- `@dhee/mcp` — MCP host/client ([`MCP_SPEC.md`](MCP_SPEC.md)).
- `@dhee/workspace` — filesystem/terminal/git/editor engines.
- `@dhee/ui` — shared, accessible UI components ([`DESIGN_SYSTEM.md`](DESIGN_SYSTEM.md)).
- `@dhee/db` — schema, migrations, and typed data access ([`DATABASE_SCHEMA.md`](DATABASE_SCHEMA.md)).
- `@dhee/testing` — shared test utilities and fixtures.

## Dependency rules (enforced)
- **Apps depend on packages; packages never depend on apps.**
- **No cyclic dependencies** between packages. The dependency graph is a DAG.
- Layered direction: `ui`/clients -> feature packages -> `core`/`config` (foundational).
  Foundational packages must not depend on higher-level ones.
- Only `@dhee/ai-provider` may call external model vendors.
- Cross-package use goes through published package entry points, never deep internal paths.
- Import boundaries are enforced by lint rules in CI ([`CI_CD.md`](CI_CD.md)).

## Versioning & releases
- Packages follow SemVer ([`VERSIONING.md`](VERSIONING.md)); releases are coordinated via the
  monorepo release tooling. Internal packages may be versioned in lockstep; public SDKs are
  versioned independently with explicit compatibility ranges.

## Build graph
- Turborepo defines task pipelines (`build`, `lint`, `test`, `typecheck`) with caching and
  correct topological ordering derived from the dependency graph.

## Adding a package or app
Per the Living Specification Rule: specify it first (its purpose, contract, and dependencies),
add/adjust an ADR if it changes architecture, then scaffold it following the naming and boundary
rules above.
