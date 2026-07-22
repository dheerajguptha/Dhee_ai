# Cursor Rules

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, CLAUDE.md
Related Documents: .cursor/rules/dhee-ai-spec.mdc, PRINCIPLES.md, NAMING.md
Next Expansion: Add file-scoped rules (e.g. TypeScript, React) once code lands in apps/ and packages/.
Last Updated: 2026-07-23
```

This is the human-readable Cursor rules document. It mirrors and expands the always-apply rule
at [`.cursor/rules/dhee-ai-spec.mdc`](.cursor/rules/dhee-ai-spec.mdc), which Cursor loads
automatically in every session. The full agent contract is in [`CLAUDE.md`](CLAUDE.md); both
derive authority from [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md).

## How rules are enforced
- **Always-apply rule:** `.cursor/rules/dhee-ai-spec.mdc` (`alwaysApply: true`) injects the
  core rules into every Cursor conversation.
- **File-scoped rules:** future `.cursor/rules/*.mdc` files will target `**/*.ts`, `**/*.tsx`,
  etc., as the codebase grows.
- **This document:** the canonical, reviewable explanation of those rules.

## The rules

1. **Specification is the source of truth.** Read the relevant specs before editing. Respect
   the precedence hierarchy in [`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md).
2. **Living Specification Rule.** Update the specification before changing behavior.
3. **No placeholder code** where a practical implementation is possible.
4. **Strict TypeScript.** No `any` in shipped code; fully typed public APIs.
5. **Tests and docs ship with every feature.**
6. **Respect module boundaries.** No cyclic dependencies; correct dependency direction.
7. **Composition over inheritance; interfaces over concretes** at boundaries.
8. **Never rewrite architecture unless explicitly requested.**
9. **Never move files without updating every reference.**
10. **No duplicated business logic.**
11. **Atomic commits**, Conventional Commits format (see [`NAMING.md`](NAMING.md)).
12. **Follow naming conventions** repository-wide ([`NAMING.md`](NAMING.md)).
13. **Secure by default;** never log secrets; validate all external input.
14. **Accessible UIs** (WCAG 2.2 AA).
15. **Refuse Constitution-violating changes;** propose a compliant alternative.

## Working style in Cursor
- Prefer Plan mode for large or ambiguous tasks; produce a plan before editing.
- Work one document/unit at a time; commit at clean boundaries (Execution Policy).
- Keep the plan, todos, and `CHANGELOG.md` synchronized with reality.

## Attribution
Do not add the AI as an author, contributor, co-author, or maintainer anywhere, and do not add
`Co-authored-by` trailers to commits.
