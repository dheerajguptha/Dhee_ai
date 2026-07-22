# Security Model (Technical)

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, PRINCIPLES.md
Related Documents: SECURITY_POLICIES.md, AUTH_SYSTEM.md, PLUGIN_SDK.md, ERROR_STANDARDS.md
Next Expansion: Complete the threat model and sandboxing specification per subsystem.
Last Updated: 2026-07-23
```

## Purpose
Define the technical security architecture of Dhee_AI (the *how*), complementing the
organizational policy in [`SECURITY_POLICIES.md`](SECURITY_POLICIES.md) (the *what/why*).

## Scope
Trust boundaries, authn/authz mechanisms, sandboxing, data protection, and threat mitigations.

## Design intent
- **Trust boundaries:** clients, edge, core, workspace, and data layers with explicit,
  least-privilege interfaces ([`ARCHITECTURE.md`](ARCHITECTURE.md)).
- **AuthN/AuthZ:** tokens, sessions, and RBAC as specified in
  [`AUTH_SYSTEM.md`](AUTH_SYSTEM.md); deny by default.
- **Sandboxing:** untrusted code (plugins, tools, computer/browser use) runs isolated with
  constrained capabilities ([`PLUGIN_SDK.md`](PLUGIN_SDK.md)); Human Override for side effects.
- **Data protection:** encryption in transit and at rest; secrets never logged; input validated
  at every boundary.
- **Isolation:** strict multi-tenant isolation.

## Threat modeling
New subsystems undergo STRIDE-style threat modeling; significant decisions recorded as ADRs
([`DECISIONS.md`](DECISIONS.md)). Errors follow [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md) so
failures are safe and non-leaking.

## Verification
Security is validated via tests, dependency/secret scanning, and reviews
([`CI_CD.md`](CI_CD.md)); it is part of the Definition of Done.
