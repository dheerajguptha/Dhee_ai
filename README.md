# Dhee_AI

> An open-source **AI Operating System** — a specification-first, agent-native platform that
> unifies chat, coding, an IDE, terminals, git, multi-agent runtimes, memory, RAG, plugins, and
> MCP into one extensible system.

**This repository is the Engineering Constitution of Dhee_AI.** It is not documentation about
the software; it *is* the source of truth from which all implementation flows. The
specification always takes precedence over code.

If you are an AI coding agent (Cursor, Claude Code, Codex, GitHub Copilot) or a human
contributor: **read [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) and
[`CLAUDE.md`](CLAUDE.md) first.**

---

## Philosophy: the specification is the constitution

Great products are not built from a single prompt. They are built from product vision, PRDs,
architecture decision records, technical specifications, coding standards, and roadmaps. This
repository captures all of that so any contributor can work autonomously while staying aligned.

- Implementation always follows specification; specification never follows implementation
  (the **Living Specification Rule**).
- When documents conflict, the higher-ranked document wins (the **precedence hierarchy**).
- No placeholder code where a practical implementation is possible; tests and docs ship with
  every feature.

### Document precedence (highest wins)
1. Engineering Constitution -> 2. Architecture -> 3. ADR Decisions -> 4. Product Requirements
-> 5. Roadmap -> 6. Milestones -> 7. Implementation.
An ADR in [`DECISIONS.md`](DECISIONS.md) is the only way to explicitly supersede a higher document.

---

## Document index

### Constitution & governance
- [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) — supreme document; precedence, quality gates, Definition of Done, Execution Policy, Living Specification Rule.
- [`PRINCIPLES.md`](PRINCIPLES.md) — the 17 constitutional principles.
- [`DECISIONS.md`](DECISIONS.md) — Architecture Decision Records (ADRs).
- [`FEATURE_MATRIX.md`](FEATURE_MATRIX.md) — master capability matrix.
- [`NAMING.md`](NAMING.md) — repository-wide naming conventions.
- [`VERSIONING.md`](VERSIONING.md) — SemVer, releases, deprecation, LTS.
- [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md) — universal error model.
- [`AI_CAPABILITIES.md`](AI_CAPABILITIES.md) — catalog of AI capabilities.
- [`SECURITY_POLICIES.md`](SECURITY_POLICIES.md) — organizational security policy.

### Agent & contributor contracts
- [`CLAUDE.md`](CLAUDE.md) — operating contract for AI coding agents.
- [`CURSOR_RULES.md`](CURSOR_RULES.md) — Cursor rules (also enforced via `.cursor/rules/`).
- [`CONTRIBUTING.md`](CONTRIBUTING.md) — how to contribute.
- [`CHANGELOG.md`](CHANGELOG.md) — notable changes.

### Product
- [`PRODUCT_VISION.md`](PRODUCT_VISION.md) — vision, mission, personas, competitive analysis.
- [`MASTER_PRD.md`](MASTER_PRD.md) — product requirements.
- [`ROADMAP.md`](ROADMAP.md) — phases and milestones.

### Architecture
- [`ARCHITECTURE.md`](ARCHITECTURE.md) — high-level architecture, boundaries, data flow.
- [`TECH_STACK.md`](TECH_STACK.md) — pinned stack and rationale.
- [`MONOREPO_STRUCTURE.md`](MONOREPO_STRUCTURE.md) — `apps/*` and `packages/*` layout.

### Technical specifications
- Data & API: [`DATABASE_SCHEMA.md`](DATABASE_SCHEMA.md), [`API_SPEC.md`](API_SPEC.md), [`AUTH_SYSTEM.md`](AUTH_SYSTEM.md)
- AI: [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md), [`AGENT_RUNTIME.md`](AGENT_RUNTIME.md), [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md), [`RAG_SYSTEM.md`](RAG_SYSTEM.md)
- Platform: [`PLUGIN_SDK.md`](PLUGIN_SDK.md), [`MCP_SPEC.md`](MCP_SPEC.md), [`WORKFLOW_ENGINE.md`](WORKFLOW_ENGINE.md)
- IDE: [`TERMINAL_ENGINE.md`](TERMINAL_ENGINE.md), [`FILESYSTEM_ENGINE.md`](FILESYSTEM_ENGINE.md), [`EDITOR_ENGINE.md`](EDITOR_ENGINE.md), [`GIT_ENGINE.md`](GIT_ENGINE.md)
- Experience: [`UI_UX_SPEC.md`](UI_UX_SPEC.md), [`DESIGN_SYSTEM.md`](DESIGN_SYSTEM.md), [`ACCESSIBILITY.md`](ACCESSIBILITY.md)
- Quality & ops: [`SECURITY_MODEL.md`](SECURITY_MODEL.md), [`TESTING_STRATEGY.md`](TESTING_STRATEGY.md), [`OBSERVABILITY.md`](OBSERVABILITY.md), [`DEPLOYMENT.md`](DEPLOYMENT.md), [`DOCKER.md`](DOCKER.md), [`KUBERNETES.md`](KUBERNETES.md), [`CI_CD.md`](CI_CD.md)

### Milestones
- [`milestones/`](milestones/README.md) — milestone index, template, and `MILESTONE_01..50`.

---

## Repository layout

```
Dhee_ai/
  ENGINEERING_CONSTITUTION.md   # supreme document
  <governance & agent contracts>
  <product, architecture, and technical specs>
  .cursor/rules/                # always-apply Cursor rule
  .github/                      # PR/issue/security templates
  milestones/                   # MILESTONE_01..50 + index
  packages/                     # shared libraries (placeholder)
  apps/                         # deployable apps (placeholder)
```

## Status

Early specification phase. The foundation, governance, product, and architecture documents are
authored; the remaining technical specifications are scaffolded and being expanded per the
Execution Policy. Each document carries a status header — see
[`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) section 3.

---

## Handoff prompt for coding agents

When you are ready to begin implementation, point your agent at this repository and say:

> Read the entire specification. Follow every document as the source of truth. Build Dhee_AI
> milestone by milestone. Never violate the architecture. Never introduce placeholder code.
> Keep the repository production-ready, tested, documented, and modular. Respect the document
> precedence hierarchy and the Living Specification Rule: update the relevant specification
> before changing behavior.

## License

To be finalized by the repository owner (Open Source First — see [`PRINCIPLES.md`](PRINCIPLES.md)).
