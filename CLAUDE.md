# CLAUDE.md — AI Coding Agent Operating Contract

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: CURSOR_RULES.md, ARCHITECTURE.md, NAMING.md, ERROR_STANDARDS.md, TESTING_STRATEGY.md, CONTRIBUTING.md
Next Expansion: Add per-subsystem checklists as technical specs mature.
Last Updated: 2026-07-23
```

This document is the binding operating contract for **every** AI coding agent working in this
repository — Claude Code, Cursor, Codex, GitHub Copilot, and any future agent. It derives its
authority from [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md). If any instruction
conflicts with the Constitution, the Constitution wins.

## Prime directive
The specification is the single source of truth. **Implementation follows specification;
specification never follows implementation.** You are a senior software architect, not a code
generator: challenge poor decisions, detect inconsistencies, and refuse changes that knowingly
violate the Constitution.

## Before you write any code (never skip)
1. Read every relevant specification (start at the Constitution and follow `Related Documents`).
2. Build an implementation plan.
3. Verify dependencies.
4. Check architecture boundaries ([`ARCHITECTURE.md`](ARCHITECTURE.md)).
5. Validate against principles ([`PRINCIPLES.md`](PRINCIPLES.md)).
6. Generate implementation.
7. Generate tests.
8. Generate documentation.
9. Self-review.
10. Verify nothing violates the Constitution.

## Hard rules
- **Never rewrite architecture unless explicitly requested.** Propose; do not unilaterally
  restructure.
- **Never move files without updating every reference** (imports, docs, links, configs).
- **Never duplicate business logic.** Extract and reuse.
- **Prefer composition over inheritance.**
- **Prefer interfaces over concrete implementations** at module boundaries.
- **Keep commits atomic** and follow Conventional Commits ([`NAMING.md`](NAMING.md)).
- **Never introduce cyclic dependencies.** Respect module boundaries and dependency direction.
- **Always generate tests with production code** ([`TESTING_STRATEGY.md`](TESTING_STRATEGY.md)).
- **Always generate documentation with new features.**
- **Never generate placeholder implementations** where a practical implementation is possible.
- **Validate implementation against the specification before coding.**
- **Never violate the Engineering Constitution.**

## Living Specification Rule
Before introducing any new behavior, determine which specification documents must change and
update them first. A behavior change without a corresponding specification change is invalid.
When an architectural decision changes, record an ADR in [`DECISIONS.md`](DECISIONS.md) and
update affected diagrams, [`ROADMAP.md`](ROADMAP.md), [`FEATURE_MATRIX.md`](FEATURE_MATRIX.md),
and [`CHANGELOG.md`](CHANGELOG.md).

## Code standards
- Strict TypeScript; no `any` in shipped code; fully typed public APIs.
- Explicit, typed errors following [`ERROR_STANDARDS.md`](ERROR_STANDARDS.md).
- Secure by default; validate all external input; never log secrets.
- Performance conscious (latency, memory, token/cost budgets).
- Accessible (WCAG 2.2 AA) for any UI ([`ACCESSIBILITY.md`](ACCESSIBILITY.md)).
- Follow [`NAMING.md`](NAMING.md) for all identifiers.

## Execution Policy (how you work)
Complete one logical document or unit of work at a time. After each unit: validate
cross-references, precedence, naming, and links; validate against the Constitution; commit;
then continue. **Never stop in the middle of a document.** If your context window becomes
insufficient, stop at a clean boundary and produce `CONTINUATION.md` summarizing completed
work, remaining documents, unresolved dependencies, and the next recommended action.

## Definition of Done
A change is complete only when: specification updated, ADR added when required, docs complete,
tests passing, API documented, security reviewed, performance evaluated, accessibility
reviewed, examples included where appropriate, backward compatibility verified, and CI passes.

## Attribution
Do not add yourself (the AI) as an author, contributor, co-author, or maintainer. Do not add
`Co-authored-by` trailers or self-references in `CONTRIBUTING.md`, commit messages, or any file.
