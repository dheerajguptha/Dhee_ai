# Authentication & Authorization System

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, SECURITY_MODEL.md, ARCHITECTURE.md
Related Documents: API_SPEC.md, DATABASE_SCHEMA.md, SECURITY_POLICIES.md, ERROR_STANDARDS.md
Next Expansion: Specify token formats, session lifecycle, and the RBAC permission catalog.
Last Updated: 2026-07-23
```

## Purpose
Define how identities are authenticated and how access is authorized across Dhee_AI, secure by
default and least-privilege.

## Scope
Authentication methods, session/token management, RBAC, API keys, multi-tenancy, and integration
with the API and data model.

## Authentication (design intent)
- Email/password with strong hashing, OAuth/OIDC providers, and optional MFA.
- Short-lived access tokens with refresh; secure, HTTP-only cookies for web clients.
- Machine access via scoped API keys ([`API_SPEC.md`](API_SPEC.md)).

## Authorization (RBAC)
- Roles and permissions scoped to organization, team, workspace, and resource levels.
- Deny by default; explicit grants; `AUTHZ.*` errors on failure
  ([`ERROR_STANDARDS.md`](ERROR_STANDARDS.md)).
- Human Override actions require appropriate permissions and are audited.

## Multi-tenancy
Strict tenant isolation at the data layer ([`DATABASE_SCHEMA.md`](DATABASE_SCHEMA.md)); no
cross-tenant access without explicit sharing.

## Security posture
No user enumeration; rate-limited auth endpoints; key rotation and secrets handling per
[`SECURITY_POLICIES.md`](SECURITY_POLICIES.md); threat model per
[`SECURITY_MODEL.md`](SECURITY_MODEL.md).

## Auditability
All authentication and authorization decisions of consequence are recorded for audit
([`OBSERVABILITY.md`](OBSERVABILITY.md)).
