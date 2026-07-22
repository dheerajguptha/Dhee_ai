# Contributing to Dhee_AI

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md, NAMING.md, VERSIONING.md
Related Documents: CLAUDE.md, CURSOR_RULES.md, TESTING_STRATEGY.md, CI_CD.md, DECISIONS.md
Next Expansion: Add a full local development setup once apps/ and packages/ are scaffolded.
Last Updated: 2026-07-23
```

Thank you for your interest in contributing. Dhee_AI is built like a real open-source project:
specification-first, tested, documented, and modular. Please read
[`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md) before contributing — it is
binding on all contributions, human and AI.

## Golden rules
- The specification is the source of truth. **Update the specification before changing
  behavior** (Living Specification Rule).
- Respect the document precedence hierarchy and module boundaries.
- No placeholder code where a practical implementation is possible.
- Tests and documentation ship with every change.

## Contribution workflow
1. **Discuss first** for anything non-trivial: open an issue (see `.github/ISSUE_TEMPLATE/`).
2. **Branch** from `main` using the naming convention in [`NAMING.md`](NAMING.md)
   (`feat/…`, `fix/…`, `docs/…`, `chore/…`).
3. **Follow the autonomous engineering workflow** in the Constitution (read specs -> plan ->
   implement -> tests -> docs -> self-review -> verify compliance).
4. **Record decisions:** if you make an architectural decision, add an ADR to
   [`DECISIONS.md`](DECISIONS.md).
5. **Update living documents** as applicable: [`CHANGELOG.md`](CHANGELOG.md),
   [`ROADMAP.md`](ROADMAP.md), [`FEATURE_MATRIX.md`](FEATURE_MATRIX.md).
6. **Open a pull request** using the PR template. Ensure every Definition of Done and quality
   gate item is satisfied.

## Commit messages
Use [Conventional Commits](https://www.conventionalcommits.org/): `type(scope): subject` in the
imperative mood. Types and rules are defined in [`NAMING.md`](NAMING.md). Breaking changes
require a `!`, a `BREAKING CHANGE:` footer, an ADR, and a [`VERSIONING.md`](VERSIONING.md)
update.

## Code quality
- Strict TypeScript; fully typed public APIs; no `any` in shipped code.
- Follow [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md), [`TESTING_STRATEGY.md`](TESTING_STRATEGY.md),
  and [`ACCESSIBILITY.md`](ACCESSIBILITY.md).
- CI must pass (see [`CI_CD.md`](CI_CD.md)).

## Reviews
Reviews are defect-first and Constitution-first. A change that is technically fine but
constitutionally invalid will not be merged. Reviewers verify architecture compliance, tests,
docs, security, performance, accessibility, and backward compatibility.

## Security
Never commit secrets. Report vulnerabilities privately per
[`SECURITY_POLICIES.md`](SECURITY_POLICIES.md) and [`.github/SECURITY.md`](.github/SECURITY.md).

## Code of conduct
Be respectful and collaborative (principle: Community Driven). A formal `CODE_OF_CONDUCT.md`
will be added by the maintainers.

## Maintainers & contributors
The maintainers and contributors list is curated by the repository owner. Automated tooling and
AI assistants are **not** listed as contributors or maintainers.
