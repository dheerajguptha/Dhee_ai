# Testing Strategy

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md, TECH_STACK.md
Related Documents: CI_CD.md, ACCESSIBILITY.md, SECURITY_MODEL.md, ERROR_STANDARDS.md
Next Expansion: Define coverage targets, test data strategy, and AI-output evaluation harnesses.
Last Updated: 2026-07-23
```

## Purpose
Ensure quality and confidence through a comprehensive, automated testing strategy (Test Before
Merge). Tests ship with every feature.

## Scope
Unit, integration, end-to-end, accessibility, performance, security, and AI-output evaluation.

## Test levels (design intent)
- **Unit:** fast, isolated tests for functions/modules (Vitest/Jest).
- **Integration:** cross-module and service/database interactions.
- **End-to-end:** user flows through the product (Playwright).
- **Accessibility:** automated + manual checks ([`ACCESSIBILITY.md`](ACCESSIBILITY.md)).
- **Performance:** budgets and benchmarks for critical paths.
- **Security:** dependency/secret scans and abuse-case tests ([`SECURITY_MODEL.md`](SECURITY_MODEL.md)).
- **AI evaluation:** deterministic harnesses and evals for provider/agent behavior, tolerant of
  model nondeterminism.

## Standards
Meaningful assertions over coverage theater; deterministic, isolated tests; typed fixtures in
`@dhee/testing`. Error paths tested per [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md).

## Enforcement
CI runs the full suite and gates merges ([`CI_CD.md`](CI_CD.md)); a change is not done until its
tests pass.
