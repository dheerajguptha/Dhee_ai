# Terminal Engine

```
Status: Draft
Priority: Medium
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, SECURITY_MODEL.md
Related Documents: FILESYSTEM_ENGINE.md, AGENT_RUNTIME.md, GIT_ENGINE.md
Next Expansion: Define the PTY protocol, session model, and agent command policy.
Last Updated: 2026-07-23
```

## Purpose
Provide an integrated terminal for users and agents to run commands in a workspace, safely and
observably.

## Scope
PTY sessions, streaming I/O, session lifecycle, and agent-driven command execution under Human
Override.

## Design intent
- **Sessions:** multiplexed PTY sessions bound to a workspace with resource limits.
- **Streaming:** low-latency, bidirectional I/O over the streaming transport
  ([`API_SPEC.md`](API_SPEC.md)).
- **Agent commands:** agents may propose commands; side-effecting or destructive commands
  require confirmation ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).

## Security
Commands run sandboxed with least privilege ([`SECURITY_MODEL.md`](SECURITY_MODEL.md)); dangerous
operations are gated and audited ([`OBSERVABILITY.md`](OBSERVABILITY.md)); secrets are never
echoed to logs.
