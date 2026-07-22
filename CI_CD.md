# CI/CD

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, TESTING_STRATEGY.md, VERSIONING.md
Related Documents: DOCKER.md, KUBERNETES.md, SECURITY_POLICIES.md, MONOREPO_STRUCTURE.md
Next Expansion: Define the concrete GitHub Actions workflows and release automation.
Last Updated: 2026-07-23
```

## Purpose
Define continuous integration and delivery so every change is validated against the quality gates
and released safely.

## Scope
CI pipelines, quality gates, artifact builds, and release automation, on GitHub Actions.

## CI pipeline (design intent)
On every pull request:
- Install (pnpm) and restore Turborepo cache.
- Typecheck, lint (including import-boundary rules from
  [`MONOREPO_STRUCTURE.md`](MONOREPO_STRUCTURE.md)), and format check.
- Run unit, integration, and e2e tests ([`TESTING_STRATEGY.md`](TESTING_STRATEGY.md)).
- Accessibility and security scans (dependencies, secrets)
  ([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)).
- Build affected apps/packages and container images ([`DOCKER.md`](DOCKER.md)).

## Quality gates
Merges are blocked unless all Repository Quality Gates in
[`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) pass. The Definition of Done is
enforced in CI where automatable.

## CD & releases
Versioning and changelog derived from Conventional Commits ([`VERSIONING.md`](VERSIONING.md));
tagged releases build and publish signed artifacts and deploy via Docker/Kubernetes
([`DEPLOYMENT.md`](DEPLOYMENT.md)) with health-gated rollouts.
