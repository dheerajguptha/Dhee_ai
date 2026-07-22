# Architecture Decision Records (ADRs)

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: ARCHITECTURE.md, TECH_STACK.md, MONOREPO_STRUCTURE.md, AI_PROVIDER_LAYER.md
Next Expansion: Add ADRs for database engine choice, auth strategy, and plugin sandboxing model.
Last Updated: 2026-07-23
```

This file is the repository-wide **Architecture Decision Record** log. An ADR captures a
significant architectural choice, its context, and its consequences. Per the
[`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md), an ADR is the **only** mechanism
that may explicitly supersede a higher-precedence document, and every major architectural
evolution must be recorded here.

## How to add an ADR

1. Copy the template below.
2. Use the next sequential number (`Decision-NNNN`, zero-padded to four digits).
3. Set `Status` to `Proposed`; change to `Accepted`, `Rejected`, `Deprecated`, or
   `Superseded by Decision-NNNN` as it evolves.
4. Never edit the meaning of an accepted ADR in place — supersede it with a new ADR.

## ADR template

```md
# Decision-NNNN: Title

- **Date:** YYYY-MM-DD
- **Status:** Proposed | Accepted | Rejected | Deprecated | Superseded by Decision-NNNN

## Context
What is the problem, force, or constraint that requires a decision?

## Decision
The choice that was made, stated in the active voice.

## Consequences
Positive, negative, and neutral results of the decision.

## Alternatives Considered
Other options and why they were not chosen.

## References
Links to specs, issues, discussions, or prior ADRs.
```

---

# Decision-0001: The specification repository is the Engineering Constitution

- **Date:** 2026-07-23
- **Status:** Accepted

## Context
Dhee_AI is an ambitious, long-lived AI Operating System. Building it from single prompts
produces inconsistent, unmaintainable results. Serious engineering organizations build from
PRDs, ADRs, technical specifications, standards, and roadmaps.

## Decision
This repository is treated as the project's Engineering Constitution and single source of
truth. Specification always precedes and outranks implementation.

## Consequences
- All contributors and AI agents must read and follow the specification before coding.
- Implementation may never evolve faster than the specification (Living Specification Rule).
- Slightly more up-front documentation cost, dramatically lower long-term maintenance cost.

## Alternatives Considered
- **Code-first with docs later:** rejected; leads to drift and undocumented behavior.
- **Single mega-prompt:** rejected; exceeds reliable generation and context limits.

## References
- [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md)

---

# Decision-0002: TypeScript monorepo with pnpm and Turborepo

- **Date:** 2026-07-23
- **Status:** Accepted

## Context
The product spans a web IDE, backend services, SDKs, a CLI, and shared libraries that must
share types and evolve together with fast, cacheable builds.

## Decision
Use a single TypeScript monorepo managed with pnpm workspaces and Turborepo, with `apps/*`
for deployables and `packages/*` for shared libraries.

## Consequences
- End-to-end type safety and shared tooling across all surfaces.
- Cacheable, parallel builds; enforced module boundaries.
- Requires discipline around dependency direction and versioning.

## Alternatives Considered
- **Polyrepo:** rejected; harder to share types and coordinate changes.
- **Nx / Bazel:** viable; Turborepo chosen for simplicity and JS/TS ergonomics. Revisit via a
  future ADR if scale demands it.

## References
- [`TECH_STACK.md`](TECH_STACK.md), [`MONOREPO_STRUCTURE.md`](MONOREPO_STRUCTURE.md)

---

# Decision-0003: Provider-agnostic AI layer

- **Date:** 2026-07-23
- **Status:** Accepted

## Context
Principle "Zero Vendor Lock-In" requires that no single model vendor is mandatory, and the
product must support cloud and local models.

## Decision
Introduce a unified AI provider abstraction that normalizes chat, streaming, tool calling,
embeddings, vision, and structured output across many providers (OpenAI, Anthropic, Google AI
Studio, Groq, OpenRouter, Ollama, Azure OpenAI, Vertex AI, AWS Bedrock).

## Consequences
- Users can switch providers or self-host without application changes.
- Requires a capability model to handle provider feature differences.

## Alternatives Considered
- **Single-provider SDK:** rejected; violates vendor independence.

## References
- [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md), [`AI_CAPABILITIES.md`](AI_CAPABILITIES.md)

---

# Decision-0004: No TODO markers; documents use a standard status header

- **Date:** 2026-07-23
- **Status:** Accepted

## Context
`TODO` markers in specifications are frequently misread by coding agents as implementation
work, producing premature or placeholder code.

## Decision
Specifications contain no `TODO` markers. Each document begins with a standard status header
and expresses incompleteness only via `Status` and `Next Expansion`.

## Consequences
- Agents treat specs as design intent, not a work queue.
- Document maturity is explicit and auditable.

## Alternatives Considered
- **Inline TODOs:** rejected for the reasons above.

## References
- [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) section 3
