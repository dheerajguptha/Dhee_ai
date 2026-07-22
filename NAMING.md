# Naming Conventions

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md
Related Documents: MONOREPO_STRUCTURE.md, DATABASE_SCHEMA.md, API_SPEC.md, PLUGIN_SDK.md, AGENT_RUNTIME.md
Next Expansion: Add linting rules that mechanically enforce each convention.
Last Updated: 2026-07-23
```

Consistent naming is a constitutional requirement. These conventions apply repository-wide and
are enforced in review and, where possible, by linters. When in doubt, prefer explicit,
descriptive names over abbreviations (principle: Explicit Over Implicit).

## Packages
- Scoped npm names: `@dhee/<name>`, lowercase, kebab-case (`@dhee/ai-provider`).
- Directory under `packages/` matches the unscoped name (`packages/ai-provider`).

## Applications
- Directory under `apps/`, lowercase, kebab-case (`apps/web`, `apps/api`, `apps/cli`).
- Deployable name mirrors the directory.

## APIs (HTTP/REST)
- Resource paths: plural nouns, kebab-case, versioned: `/v1/chat-sessions`.
- Query params: `camelCase`. JSON fields: `camelCase`.
- No verbs in resource paths; use HTTP methods. Actions use a sub-resource: `POST /v1/agents/{id}/runs`.

## Events
- Format: `domain.entity.action` in past tense, dot-delimited, lowercase:
  `agent.run.completed`, `memory.item.created`.

## Commands (CLI + command palette)
- CLI subcommands: kebab-case (`dhee agent run`).
- Internal command IDs: `namespace.action` (`editor.formatDocument`).

## TypeScript identifiers
- Types, interfaces, classes, enums: `PascalCase`. Do not prefix interfaces with `I`.
- Variables, functions, methods: `camelCase`.
- Constants (module-level, truly constant): `UPPER_SNAKE_CASE`.
- Files: `kebab-case.ts`; React components: `PascalCase.tsx`.
- Test files: `*.test.ts` (unit/integration), `*.e2e.ts` (end-to-end).

## React components & hooks
- Components: `PascalCase` (`ChatPanel`).
- Hooks: `use` + `PascalCase` (`useChatSession`).
- Context providers: `<Name>Provider`; context value type: `<Name>ContextValue`.

## Database tables & columns
- Tables: plural, `snake_case` (`chat_sessions`).
- Columns: `snake_case` (`created_at`). Primary key: `id`. Foreign key: `<entity>_id`.
- Timestamps: `created_at`, `updated_at`, `deleted_at` (soft delete).
- Booleans: `is_`/`has_` prefix (`is_archived`).
- Enums: singular `snake_case` type name.

## Environment variables
- `UPPER_SNAKE_CASE`, prefixed by domain: `DHEE_DATABASE_URL`, `DHEE_OPENAI_API_KEY`.
- Never commit secrets; document every variable in `.env.example`.

## Agents
- Agent IDs: kebab-case (`backend-agent`); display names: Title Case (`Backend Agent`).
- Custom agents follow the same rule and must not collide with built-in IDs.

## SDKs
- Packages: `@dhee/<x>-sdk` (`@dhee/plugin-sdk`, `@dhee/provider-sdk`, `@dhee/tool-sdk`).

## Plugins
- Plugin IDs: reverse-DNS-like, kebab-case: `publisher.plugin-name`.
- Entry manifest field names follow the plugin manifest schema in
  [`PLUGIN_SDK.md`](PLUGIN_SDK.md).

## Files & directories
- Directories: kebab-case. Source files: kebab-case. One primary export concept per file.
- Markdown specs at repo root: `UPPER_SNAKE_CASE.md` (e.g. `API_SPEC.md`); milestones:
  `MILESTONE_NN.md`.

## Branches
- `main` is the trunk.
- Feature: `feat/<area>-<short-desc>`; fix: `fix/<area>-<short-desc>`;
  docs: `docs/<short-desc>`; chore: `chore/<short-desc>`.

## Commit messages
- Conventional Commits: `type(scope): subject` in imperative mood.
- Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, `perf`, `build`, `ci`.
- Breaking changes: append `!` and add a `BREAKING CHANGE:` footer; requires an ADR and a
  [`VERSIONING.md`](VERSIONING.md) update.
