# MCP Specification

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, PLUGIN_SDK.md, SECURITY_MODEL.md
Related Documents: AGENT_RUNTIME.md, AI_PROVIDER_LAYER.md, VERSIONING.md
Next Expansion: Pin the supported MCP protocol version(s) and define host/client capabilities.
Last Updated: 2026-07-23
```

## Purpose
Define Dhee_AI's compatibility with the Model Context Protocol (MCP) so external tools,
resources, and prompts can be used by agents through a standard, interoperable interface.

## Scope
MCP client and host roles, transport, capability negotiation, tool/resource/prompt exposure, and
security.

## Roles (design intent)
- **MCP client/host:** Dhee_AI connects to external MCP servers to discover and invoke tools and
  read resources, surfacing them to the agent runtime ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).
- **MCP server (optional):** Dhee_AI may expose selected capabilities as an MCP server.

## Transport & negotiation
Support standard MCP transports; negotiate protocol version and capabilities on connect. The
supported version range is declared per release ([`VERSIONING.md`](VERSIONING.md)).

## Mapping to Dhee_AI
MCP tools map onto the Tool SDK contract ([`PLUGIN_SDK.md`](PLUGIN_SDK.md)); MCP resources feed
retrieval/context; MCP prompts integrate with the prompt compiler.

## Security
MCP connections are least-privilege and user-approved; tool invocations respect Human Override
and sandboxing ([`SECURITY_MODEL.md`](SECURITY_MODEL.md)); untrusted servers are treated as
hostile input.
