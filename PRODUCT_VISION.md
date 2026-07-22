# Product Vision

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: MASTER_PRD.md, FEATURE_MATRIX.md, ROADMAP.md, ARCHITECTURE.md
Next Expansion: Add quantified success metrics and a north-star metric once early usage exists.
Last Updated: 2026-07-23
```

## Vision
A world where anyone can direct powerful, trustworthy AI to build, operate, and understand
software — through an open platform they fully control.

## Mission
Build **Dhee_AI**, an open-source AI Operating System that unifies conversation, coding, an
IDE, terminals, git, multi-agent execution, memory, retrieval, plugins, and MCP into one
coherent, extensible, self-hostable system — with humans always in control.

## Philosophy
Dhee_AI is built on the conviction that the *specification* is more valuable than any single
implementation. Code changes; architecture and product vision endure. We build like a serious
engineering organization: vision, PRDs, ADRs, specs, standards, and roadmaps first — then
implementation that never outpaces the specification. See
[`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) and [`PRINCIPLES.md`](PRINCIPLES.md).

## What Dhee_AI is
- An **AI Operating System**: a platform where AI is a first-class runtime, not a feature.
- **Agent-native**: specialized agents plan and execute real work under human oversight.
- **Provider-agnostic**: many model providers and local models, no vendor lock-in.
- **Extensible**: plugins, SDKs, and MCP make it a platform others build on.
- **Self-hostable and open**: run it yourself; own your data.

## Core principles (summary)
AI First; Human Override; Open Source First; Secure by Default; Privacy by Design; Modular
Architecture; Extensibility Before Convenience; Zero Vendor Lock-In; Backward Compatibility;
Test Before Merge; Documentation Equals Code; API First; Performance Conscious; Accessibility
First; Simplicity Over Complexity; Explicit Over Implicit; Community Driven. Full definitions in
[`PRINCIPLES.md`](PRINCIPLES.md).

## Target users (personas)
- **The Builder (individual developer).** Wants an AI-native IDE that can plan, write, refactor,
  test, and ship. Values speed, control, and local/self-hosted options.
- **The Team Lead.** Coordinates multiple developers and agents; wants shared memory, workflows,
  standards enforcement, and auditability.
- **The Enterprise Platform Owner.** Needs RBAC, audit logs, usage analytics, self-hosting,
  security, and compliance.
- **The Extension Developer.** Builds plugins, tools, and providers on the SDKs and MCP; needs
  stable, well-documented, versioned contracts.
- **The Researcher / Power User.** Runs autonomous and multi-agent workflows; needs
  transparency, reproducibility, and fine-grained control.

## Non-goals
- Not a closed, single-vendor product; no mandatory external dependency.
- Not a thin wrapper over one model API.
- Not a black box: no unauditable autonomous actions; Human Override is always available.
- Not chasing feature breadth at the expense of architectural integrity.
- Not sacrificing long-term maintainability for short-term convenience.

## Competitive analysis
Dhee_AI learns from, and differentiates against, leading tools:

- **Cursor** — excellent AI IDE. Dhee_AI differs by being open-source, self-hostable,
  provider-agnostic, and an OS-class platform (agents, memory, workflows, plugins, MCP) rather
  than an editor alone.
- **Claude Code** — strong agentic CLI coding. Dhee_AI adds a full IDE, multi-agent
  orchestration, persistent multi-scope memory, and a plugin ecosystem, across many providers.
- **OpenHands (formerly OpenDevin)** — open agent platform. Dhee_AI emphasizes a unified IDE
  experience, a formal specification constitution, and enterprise-grade governance.
- **Windsurf** — agentic IDE. Dhee_AI differentiates via openness, extensibility (SDKs/MCP),
  and vendor independence.
- **ChatGPT** — general assistant. Dhee_AI is a developer-focused OS with deep repository
  understanding, tools, memory, and self-hosting.

**Differentiators:** open source; specification-as-constitution; provider independence;
multi-agent runtime; multi-scope memory + RAG; plugin/SDK/MCP extensibility; self-hosting and
privacy; enterprise governance.

## Success metrics (directional)
- **Adoption:** installs, active workspaces, self-hosted deployments.
- **Contribution health:** external contributors, merged PRs, plugins published.
- **Productivity:** task completion rate, time-to-first-value, agent success rate.
- **Trust & quality:** incident rate, override/intervention rate, test coverage, accessibility
  conformance.
- **Independence:** share of usage on non-default providers and local models.

Quantified targets will be defined in [`MASTER_PRD.md`](MASTER_PRD.md) and refined as real
usage data becomes available.
