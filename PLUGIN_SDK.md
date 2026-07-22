# Plugin SDK

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, PRINCIPLES.md, SECURITY_MODEL.md
Related Documents: MCP_SPEC.md, AI_PROVIDER_LAYER.md, AGENT_RUNTIME.md, NAMING.md, VERSIONING.md
Next Expansion: Define the plugin manifest schema, lifecycle hooks, and permission model.
Last Updated: 2026-07-23
```

## Purpose
Provide first-class extensibility so third parties (and internal features) can add capabilities:
tools, providers, agents, and UI contributions (Extensibility Before Convenience).

## Scope
Plugin SDK, Provider SDK, Tool SDK, manifest, lifecycle, permissions, sandboxing, and
distribution/marketplace.

## SDK surfaces (design intent)
- **Plugin SDK:** register commands, tools, panels, and settings.
- **Provider SDK:** add AI providers/models to the provider layer
  ([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)).
- **Tool SDK:** define typed tools callable by agents ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).

## Manifest & lifecycle
Plugins declare identity, version, permissions, and contributions in a manifest (naming per
[`NAMING.md`](NAMING.md)). Lifecycle: install, activate, configure, update, deactivate,
uninstall. Versioning and compatibility per [`VERSIONING.md`](VERSIONING.md).

## Permissions & sandboxing
Least-privilege permissions declared up front and granted by the user; untrusted plugin code
runs sandboxed ([`SECURITY_MODEL.md`](SECURITY_MODEL.md)). Plugins cannot bypass Human Override.

## Distribution
A marketplace for discovery and installation; signed packages and provenance per
[`SECURITY_POLICIES.md`](SECURITY_POLICIES.md).

## Interoperability
MCP compatibility ([`MCP_SPEC.md`](MCP_SPEC.md)) lets external tools/resources integrate through
a standard protocol.
