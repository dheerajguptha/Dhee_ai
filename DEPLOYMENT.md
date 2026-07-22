# Deployment

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, TECH_STACK.md, PRINCIPLES.md
Related Documents: DOCKER.md, KUBERNETES.md, CI_CD.md, OBSERVABILITY.md, SECURITY_POLICIES.md
Next Expansion: Define reference topologies, configuration, and upgrade/auto-update procedures.
Last Updated: 2026-07-23
```

## Purpose
Define how Dhee_AI is packaged, deployed, and operated, both self-hosted and in the cloud, with
no mandatory proprietary dependency (Zero Vendor Lock-In).

## Scope
Deployment topologies, configuration, secrets, data services, scaling, upgrades, and
auto-updates.

## Design intent
- **Self-hosted:** single-node via Docker Compose ([`DOCKER.md`](DOCKER.md)) and multi-node via
  Kubernetes ([`KUBERNETES.md`](KUBERNETES.md)).
- **Cloud:** portable to major clouds using the same containers/manifests.
- **Configuration:** typed, validated config; secrets via environment/secret managers
  ([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)).
- **Data services:** Postgres (+ pgvector), Redis, object storage, and a job queue provisioned or
  connected per environment.
- **Scaling:** stateless services scale horizontally; workers scale independently
  ([`ARCHITECTURE.md`](ARCHITECTURE.md)).

## Upgrades & auto-updates
Zero/low-downtime upgrades with forward-only migrations ([`VERSIONING.md`](VERSIONING.md));
optional auto-update channel with rollback. Health checks and observability gate rollouts
([`OBSERVABILITY.md`](OBSERVABILITY.md)).
