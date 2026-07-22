# Feature Matrix

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, MASTER_PRD.md, ROADMAP.md
Related Documents: AI_CAPABILITIES.md, AGENT_RUNTIME.md, MEMORY_ENGINE.md, RAG_SYSTEM.md, PLUGIN_SDK.md, MCP_SPEC.md
Next Expansion: Expand each category into per-feature sub-specs as milestones are scheduled.
Last Updated: 2026-07-23
```

This is the master capability matrix for Dhee_AI, maintained separately from the PRD. It is the
authoritative list of product capabilities. Per the Living Specification Rule, any new
capability must be added here before implementation, and any capability change must update this
file.

Legend:
- **Status:** `Planned` | `In Design` | `In Progress` | `Beta` | `Stable`
- **Phase:** the roadmap phase (see [`ROADMAP.md`](ROADMAP.md))
- **Priority:** `High` | `Medium` | `Low`
- **Planned Version:** target SemVer (see [`VERSIONING.md`](VERSIONING.md))

> Presented as structured lists (not tables) for readability and clean diffs.

## Chat
- Multi-turn conversations — Status: In Design | Phase: 3 | Priority: High | Depends: AI provider layer | Version: 1.0
- Streaming responses — Status: In Design | Phase: 3 | Priority: High | Depends: provider layer | Version: 1.0
- Structured output — Status: Planned | Phase: 3 | Priority: High | Depends: provider layer | Version: 1.0
- Multimodal (vision/voice/OCR) input — Status: Planned | Phase: 3 | Priority: Medium | Depends: provider capabilities | Version: 1.1

## Coding
- Code generation — Status: Planned | Phase: 6 | Priority: High | Depends: editor engine, RAG | Version: 1.0
- AI refactoring — Status: Planned | Phase: 6 | Priority: High | Depends: editor engine, tests | Version: 1.1
- AI code review — Status: Planned | Phase: 6 | Priority: Medium | Depends: agent runtime | Version: 1.1
- AI documentation — Status: Planned | Phase: 6 | Priority: Medium | Depends: agent runtime | Version: 1.1

## IDE
- Monaco editor — Status: Planned | Phase: 6 | Priority: High | Depends: web app | Version: 1.0
- File explorer — Status: Planned | Phase: 6 | Priority: High | Depends: filesystem engine | Version: 1.0
- Diff viewer — Status: Planned | Phase: 6 | Priority: Medium | Depends: git engine | Version: 1.0
- Search (project-wide) — Status: Planned | Phase: 6 | Priority: Medium | Depends: filesystem engine | Version: 1.0
- Debugging & testing panels — Status: Planned | Phase: 6 | Priority: Medium | Depends: editor engine | Version: 1.2
- Multi-root workspaces — Status: Planned | Phase: 6 | Priority: Low | Depends: filesystem engine | Version: 1.2

## Terminal
- Integrated terminal — Status: Planned | Phase: 6 | Priority: High | Depends: terminal engine | Version: 1.0
- Agent-driven commands (with Human Override) — Status: Planned | Phase: 6 | Priority: Medium | Depends: agent runtime | Version: 1.1

## Git
- Git panel & operations — Status: Planned | Phase: 6 | Priority: High | Depends: git engine | Version: 1.0
- AI commit messages / PR summaries — Status: Planned | Phase: 6 | Priority: Medium | Depends: agent runtime | Version: 1.1

## Agents
- Manager/Planner/Architect agents — Status: In Design | Phase: 4 | Priority: High | Depends: agent runtime | Version: 1.0
- Backend/Frontend/Database/DevOps agents — Status: Planned | Phase: 4 | Priority: High | Depends: agent runtime | Version: 1.0
- Security/Testing/Documentation/Research agents — Status: Planned | Phase: 4 | Priority: Medium | Depends: agent runtime | Version: 1.1
- Browser/Computer/Deployment/Review agents — Status: Planned | Phase: 4 | Priority: Medium | Depends: tool surfaces | Version: 1.1
- Custom user-defined agents — Status: Planned | Phase: 4 | Priority: High | Depends: agent runtime, plugin SDK | Version: 1.1

## Memory
- Conversation/User/Project/Workspace/Team memory — Status: In Design | Phase: 5 | Priority: High | Depends: database, embeddings | Version: 1.0
- Long-term & semantic memory — Status: Planned | Phase: 5 | Priority: High | Depends: vector store | Version: 1.1
- Knowledge graph — Status: Planned | Phase: 5 | Priority: Medium | Depends: memory engine | Version: 1.2
- Import/export & privacy controls — Status: Planned | Phase: 5 | Priority: High | Depends: memory engine | Version: 1.0

## RAG
- Document ingestion & chunking — Status: Planned | Phase: 5 | Priority: High | Depends: embeddings, vector store | Version: 1.0
- Retrieval & reranking — Status: Planned | Phase: 5 | Priority: High | Depends: vector store | Version: 1.0
- Repository-scale indexing — Status: Planned | Phase: 5 | Priority: Medium | Depends: RAG system | Version: 1.1

## Provider Layer
- Multi-provider routing & failover — Status: In Design | Phase: 3 | Priority: High | Depends: provider SDK | Version: 1.0
- Smart model selection & token optimization — Status: Planned | Phase: 3 | Priority: High | Depends: provider layer | Version: 1.1
- Local models (Ollama) — Status: Planned | Phase: 3 | Priority: Medium | Depends: provider layer | Version: 1.0

## Plugins
- Plugin SDK & lifecycle — Status: Planned | Phase: 8 | Priority: High | Depends: sandboxing | Version: 1.1
- Tool SDK & Provider SDK — Status: Planned | Phase: 8 | Priority: High | Depends: plugin SDK | Version: 1.1
- Marketplace — Status: Planned | Phase: 8 | Priority: Medium | Depends: plugin SDK | Version: 1.2

## MCP
- MCP client/host compatibility — Status: Planned | Phase: 8 | Priority: High | Depends: plugin/tool SDK | Version: 1.1

## Security
- AuthN/AuthZ & RBAC — Status: Planned | Phase: 9 | Priority: High | Depends: auth system | Version: 1.0
- Sandboxing (plugins/computer-use) — Status: Planned | Phase: 8 | Priority: High | Depends: security model | Version: 1.1
- Audit logs — Status: Planned | Phase: 9 | Priority: High | Depends: observability | Version: 1.1

## Enterprise
- Organizations & teams — Status: Planned | Phase: 9 | Priority: Medium | Depends: auth system | Version: 1.2
- API keys, usage analytics, billing hooks — Status: Planned | Phase: 9 | Priority: Medium | Depends: API | Version: 1.2
- Admin dashboard — Status: Planned | Phase: 9 | Priority: Low | Depends: web app | Version: 1.3

## Automation
- Workflow builder — Status: Planned | Phase: 7 | Priority: High | Depends: workflow engine | Version: 1.1
- Background jobs & scheduled tasks — Status: Planned | Phase: 7 | Priority: Medium | Depends: workflow engine | Version: 1.1
- Event triggers & AI pipelines — Status: Planned | Phase: 7 | Priority: Medium | Depends: workflow engine | Version: 1.2

## Desktop
- Desktop application — Status: Planned | Phase: 10 | Priority: Low | Depends: web app | Version: 1.3

## Mobile
- Mobile companion — Status: Planned | Phase: 10 | Priority: Low | Depends: API | Version: 2.0

## API
- Public REST API — Status: Planned | Phase: 2 | Priority: High | Depends: backend | Version: 1.0
- Webhooks & streaming API — Status: Planned | Phase: 2 | Priority: Medium | Depends: API | Version: 1.1

## CLI
- `dhee` CLI — Status: Planned | Phase: 2 | Priority: Medium | Depends: API | Version: 1.0
