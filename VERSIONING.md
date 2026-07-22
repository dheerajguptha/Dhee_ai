# Versioning Policy

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md
Related Documents: CHANGELOG.md, DECISIONS.md, API_SPEC.md, PLUGIN_SDK.md, CI_CD.md
Next Expansion: Define automated release tooling (changesets) and LTS calendar once v1.0 nears.
Last Updated: 2026-07-23
```

Versioning protects the Backward Compatibility principle. This policy governs the product, all
published packages, public APIs, the plugin/SDK surface, and the MCP contract.

## Semantic Versioning
Dhee_AI follows [SemVer 2.0.0](https://semver.org/): `MAJOR.MINOR.PATCH`.

- **MAJOR** — incompatible/breaking changes.
- **MINOR** — backward-compatible new functionality.
- **PATCH** — backward-compatible bug fixes.

Pre-1.0 packages may still introduce breaking changes in MINOR, but must document them; once a
package reaches 1.0 the full guarantees apply.

## Release channels
- **Stable** — production-ready; default install target. Tagged `x.y.z`.
- **Beta** — feature-complete, undergoing hardening. Tagged `x.y.z-beta.n`.
- **Alpha** — experimental, may change without notice. Tagged `x.y.z-alpha.n`.

Pre-release identifiers follow SemVer ordering: `alpha < beta < rc < stable`.

## Breaking changes
A change is breaking if it removes or renames public API, changes behavior clients rely on,
changes data formats without migration, or tightens input/loosens output contracts. Every
breaking change requires:

1. An ADR in [`DECISIONS.md`](DECISIONS.md).
2. A `MAJOR` version bump.
3. A migration guide (see below).
4. An entry in [`CHANGELOG.md`](CHANGELOG.md) with a `BREAKING CHANGE` note.

## Deprecation policy
- Mark deprecated APIs in code and docs with the target removal version.
- Deprecations remain functional for at least **one MAJOR** cycle (or one LTS window).
- Emit runtime deprecation warnings where feasible; never remove without prior deprecation.

## Migration guides
- Every MAJOR release ships a `MIGRATION.md`-style guide describing required changes, codemods
  where possible, and before/after examples.

## Long-Term Support (LTS)
- Designated LTS releases receive security and critical bug fixes for a defined window.
- The LTS window and calendar are published alongside each LTS release.

## Compatibility guarantees
- **API:** documented endpoints in [`API_SPEC.md`](API_SPEC.md) are stable within a MAJOR.
- **Plugins/SDK:** the plugin contract in [`PLUGIN_SDK.md`](PLUGIN_SDK.md) is versioned; the
  host declares the supported plugin API range.
- **MCP:** the supported MCP version range is declared per release.
- **Data:** schema migrations are forward-only and reversible where practical; no silent data
  loss.

## Release process (summary)
1. Ensure Definition of Done and quality gates pass ([`ENGINEERING_CONSTITUTION.md`](ENGINEERING_CONSTITUTION.md)).
2. Update [`CHANGELOG.md`](CHANGELOG.md); compute the version bump from Conventional Commits.
3. Tag the release; CI builds, tests, and publishes artifacts (see [`CI_CD.md`](CI_CD.md)).
4. Publish migration notes for MAJOR releases.
