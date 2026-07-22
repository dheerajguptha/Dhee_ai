# Security Policies (Organizational)

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: SECURITY_MODEL.md, VERSIONING.md, CI_CD.md, .github/SECURITY.md
Next Expansion: Add compliance mapping (SOC 2 / ISO 27001) and formal incident-response runbook.
Last Updated: 2026-07-23
```

This document defines the **organizational** security policies for Dhee_AI. The **technical**
security architecture (authn/authz mechanisms, sandboxing, threat controls in code) lives in
[`SECURITY_MODEL.md`](SECURITY_MODEL.md). Both are binding.

## Responsible disclosure
- Report suspected vulnerabilities **privately** (GitHub Security Advisories); never in public
  issues. See [`.github/SECURITY.md`](.github/SECURITY.md).
- We acknowledge reports promptly, provide status updates, and coordinate a disclosure timeline
  with the reporter.
- Good-faith research is welcomed under safe-harbor terms: no data destruction, no privacy
  violations, no service degradation.

## Vulnerability reporting & handling
- Triage severity using CVSS.
- Track remediation with target timelines by severity (critical fastest).
- Publish advisories and credit reporters (with consent) after fixes ship.

## Dependency management
- Pin dependencies; review transitive changes.
- Automated vulnerability scanning in CI ([`CI_CD.md`](CI_CD.md)); block merges on known
  high/critical advisories.
- Prefer well-maintained, permissively licensed dependencies; minimize dependency count.

## Secrets management
- Never commit secrets. Secrets are provided via environment/secret managers; `.env` is
  git-ignored and `.env.example` documents required variables.
- CI scans for accidentally committed secrets.
- Access to production secrets is least-privilege and audited.

## Key rotation
- Rotate signing keys, API keys, and credentials on a defined schedule and immediately on
  suspected compromise.
- Support overlapping validity windows to enable zero-downtime rotation.

## Secure coding guidelines
- Validate and sanitize all external input; encode output to prevent injection/XSS.
- Use parameterized queries; never build queries by string concatenation.
- Enforce least privilege for services, tokens, and plugins.
- Sandbox untrusted code (plugins, computer-use, browser automation) per
  [`SECURITY_MODEL.md`](SECURITY_MODEL.md).
- Fail securely (deny by default) and follow [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md) so
  errors never leak sensitive data.

## Threat modeling
- New subsystems undergo threat modeling (e.g., STRIDE) during design.
- Record significant security-architecture decisions as ADRs in
  [`DECISIONS.md`](DECISIONS.md).

## Privacy principles
- Data minimization and purpose limitation.
- User control: export and delete personal/project data (see
  [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md)).
- Encrypt sensitive data in transit and at rest.

## Compliance goals
- Design toward recognized frameworks (e.g., SOC 2, ISO 27001, GDPR-aligned data handling)
  even before formal certification.

## Supply chain security
- Reproducible, verifiable builds; signed releases where feasible.
- Generate SBOMs for releases.
- Protect the CI/CD pipeline with least privilege and provenance attestation.
