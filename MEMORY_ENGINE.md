# Memory Engine

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, DATABASE_SCHEMA.md, PRINCIPLES.md
Related Documents: RAG_SYSTEM.md, AGENT_RUNTIME.md, AI_PROVIDER_LAYER.md, SECURITY_POLICIES.md
Next Expansion: Define memory schemas, scoring/decay, and the import/export format.
Last Updated: 2026-07-23
```

## Purpose
Provide persistent, multi-scope memory so agents and users retain relevant context over time,
with privacy under user control (Privacy by Design).

## Scope
Conversation, user, project, workspace, and team memory; long-term and semantic memory; a
knowledge graph; versioning; import/export; and privacy controls.

## Memory scopes (design intent)
- **Conversation:** short-term context for the current session.
- **User / Project / Workspace / Team:** durable memory scoped to each entity.
- **Long-term & semantic:** distilled, embedded knowledge retrievable by meaning.
- **Knowledge graph:** entities and relationships derived from memory.

## Retrieval
Semantic retrieval uses embeddings and pgvector, integrated with RAG
([`RAG_SYSTEM.md`](RAG_SYSTEM.md)) and the context manager
([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)).

## Lifecycle
Write, score, consolidate, and decay/forget policies keep memory relevant and bounded. Memory is
versioned for auditability and rollback.

## Privacy & control
Users can view, export, and delete their memory; data minimization and encryption apply
([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)). Team/shared memory respects RBAC
([`AUTH_SYSTEM.md`](AUTH_SYSTEM.md)).
