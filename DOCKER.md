# Docker

```
Status: Draft
Priority: Medium
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, DEPLOYMENT.md, TECH_STACK.md
Related Documents: KUBERNETES.md, CI_CD.md, SECURITY_POLICIES.md
Next Expansion: Provide Dockerfiles and a docker-compose reference stack.
Last Updated: 2026-07-23
```

## Purpose
Define container images and the single-node Docker Compose stack for running Dhee_AI.

## Scope
Image build strategy, the compose stack, configuration, and image security.

## Design intent
- **Images:** multi-stage builds producing small, non-root images per app
  ([`MONOREPO_STRUCTURE.md`](MONOREPO_STRUCTURE.md)); reproducible and pinned.
- **Compose stack:** `apps/api`, `apps/web`, Postgres (+ pgvector), Redis, object storage, and a
  worker, wired for local/self-hosted use ([`DEPLOYMENT.md`](DEPLOYMENT.md)).
- **Configuration:** environment-driven; secrets injected, never baked into images.

## Security
Non-root users, minimal base images, no secrets in layers, and image scanning in CI
([`CI_CD.md`](CI_CD.md), [`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)).
