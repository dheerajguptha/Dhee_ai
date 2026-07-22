# Dhee_AI Principles

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md
Related Documents: ARCHITECTURE.md, SECURITY_MODEL.md, SECURITY_POLICIES.md, DECISIONS.md
Next Expansion: Add worked examples of each principle applied to a real subsystem.
Last Updated: 2026-07-23
```

These are the constitutional principles of Dhee_AI. They are binding on every contributor and
every AI coding agent. When principles appear to conflict, resolve using the document
precedence hierarchy in [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) and, if
needed, record an ADR in [`DECISIONS.md`](DECISIONS.md).

Each principle below states **what it means**, **why it matters**, and **how it is enforced**.

---

## 1. AI First
- **Meaning:** AI is a primary interface and a first-class runtime capability, not a bolt-on.
- **Why:** Dhee_AI is an AI Operating System; intelligence is the product's core loop.
- **Enforcement:** Every subsystem exposes machine-usable, well-typed APIs and tool schemas so
  agents can operate it. See [`AI_CAPABILITIES.md`](AI_CAPABILITIES.md).

## 2. Human Override
- **Meaning:** A human can always inspect, pause, correct, or reverse any AI action.
- **Why:** Trust, safety, and accountability require ultimate human control.
- **Enforcement:** Destructive or irreversible actions require confirmation; all agent actions
  are logged and auditable (see [`OBSERVABILITY.md`](OBSERVABILITY.md)).

## 3. Open Source First
- **Meaning:** The project is built in the open and prefers open standards and open source.
- **Why:** Longevity, community trust, and vendor independence.
- **Enforcement:** Licenses are compatible with open distribution; proprietary dependencies are
  avoided or made optional and swappable.

## 4. Secure by Default
- **Meaning:** The safe configuration is the default configuration.
- **Why:** Most security failures come from insecure defaults.
- **Enforcement:** Least privilege, deny-by-default, encrypted secrets. See
  [`SECURITY_MODEL.md`](SECURITY_MODEL.md) and [`SECURITY_POLICIES.md`](SECURITY_POLICIES.md).

## 5. Privacy by Design
- **Meaning:** User and project data is private, minimized, and under user control.
- **Why:** Memory and RAG systems handle sensitive context.
- **Enforcement:** Data minimization, explicit consent, export/delete controls. See
  [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md).

## 6. Modular Architecture
- **Meaning:** The system is composed of independent, replaceable modules with clear
  boundaries.
- **Why:** Enables parallel work, testing, and long-term evolution.
- **Enforcement:** Module boundaries and dependency rules in
  [`ARCHITECTURE.md`](ARCHITECTURE.md) and [`MONOREPO_STRUCTURE.md`](MONOREPO_STRUCTURE.md);
  no cyclic dependencies.

## 7. Extensibility Before Convenience
- **Meaning:** Prefer designs that others can extend over shortcuts that only serve today.
- **Why:** A platform lives or dies by its extension points.
- **Enforcement:** Public extension points via [`PLUGIN_SDK.md`](PLUGIN_SDK.md) and
  [`MCP_SPEC.md`](MCP_SPEC.md); internal features prefer the same SDKs plugins use.

## 8. Zero Vendor Lock-In
- **Meaning:** No single external vendor is required to run Dhee_AI.
- **Why:** Independence and resilience.
- **Enforcement:** The provider abstraction in [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)
  supports many providers and local models; infra is portable (see
  [`DEPLOYMENT.md`](DEPLOYMENT.md)).

## 9. Backward Compatibility
- **Meaning:** Existing users and integrations keep working across upgrades.
- **Why:** Trust and adoption depend on stability.
- **Enforcement:** SemVer and deprecation policy in [`VERSIONING.md`](VERSIONING.md); breaking
  changes require an ADR and migration guide.

## 10. Test Before Merge
- **Meaning:** Code merges only with passing, meaningful tests.
- **Why:** Quality and confidence at scale.
- **Enforcement:** CI gates in [`CI_CD.md`](CI_CD.md); coverage and strategy in
  [`TESTING_STRATEGY.md`](TESTING_STRATEGY.md).

## 11. Documentation Equals Code
- **Meaning:** Documentation is a first-class deliverable shipped with every change.
- **Why:** Undocumented behavior is unmaintainable behavior.
- **Enforcement:** Definition of Done requires docs; the Living Specification Rule requires spec
  updates before behavior changes.

## 12. API First
- **Meaning:** Design the interface/contract before the implementation.
- **Why:** Clear contracts enable parallelism, testing, and stability.
- **Enforcement:** Contracts defined in [`API_SPEC.md`](API_SPEC.md) precede implementation.

## 13. Performance Conscious
- **Meaning:** Latency, memory, and cost are design constraints, not afterthoughts.
- **Why:** An OS-class product must feel instant and be affordable to run.
- **Enforcement:** Performance budgets and token optimization (see
  [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)); benchmarks in CI where relevant.

## 14. Accessibility First
- **Meaning:** The product is usable by everyone, including assistive-technology users.
- **Why:** Inclusion is a requirement, not a feature.
- **Enforcement:** WCAG 2.2 AA target in [`ACCESSIBILITY.md`](ACCESSIBILITY.md).

## 15. Simplicity Over Complexity
- **Meaning:** Choose the simplest design that satisfies the requirements.
- **Why:** Complexity is the primary long-term cost.
- **Enforcement:** Reviews reject unjustified complexity; prefer fewer moving parts.

## 16. Explicit Over Implicit
- **Meaning:** Behavior, types, and contracts are stated explicitly.
- **Why:** Implicit behavior causes surprising bugs and is hard for agents to reason about.
- **Enforcement:** Strict TypeScript, no `any`, explicit error types (see
  [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md)).

## 17. Community Driven
- **Meaning:** The project is shaped by its contributors and users.
- **Why:** A durable open-source OS is a shared effort.
- **Enforcement:** Transparent decisions (ADRs), welcoming contribution process (see
  [`CONTRIBUTING.md`](CONTRIBUTING.md)).
