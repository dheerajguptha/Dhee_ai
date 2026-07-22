# Database Schema

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, TECH_STACK.md, NAMING.md
Related Documents: API_SPEC.md, AUTH_SYSTEM.md, MEMORY_ENGINE.md, RAG_SYSTEM.md
Next Expansion: Define concrete tables, columns, indexes, and migrations for Phase 2 entities.
Last Updated: 2026-07-23
```

## Purpose
Define the relational and vector data model for Dhee_AI on PostgreSQL (+ pgvector), including
entities, relationships, indexing, and migration strategy.

## Scope
Core persistence for users, organizations, workspaces, projects, conversations, messages,
agents, agent runs, memory items, embeddings, plugins, and audit records. Object blobs live in
object storage; caches live in Redis (see [`ARCHITECTURE.md`](ARCHITECTURE.md)).

## Conventions
Tables are plural `snake_case`; columns `snake_case`; primary key `id`; foreign keys
`<entity>_id`; timestamps `created_at`/`updated_at`/`deleted_at` (soft delete). See
[`NAMING.md`](NAMING.md).

## Core entities (design intent)
- **Identity & tenancy:** `users`, `organizations`, `teams`, `memberships`, `api_keys`.
- **Workspace:** `workspaces`, `projects`, `files_index` (metadata, not blobs).
- **Conversations:** `conversations`, `messages`, `attachments`.
- **Agents:** `agents`, `agent_runs`, `agent_steps`, `tool_invocations`.
- **Memory & RAG:** `memory_items`, `embeddings` (pgvector), `documents`, `chunks`.
- **Extensibility:** `plugins`, `plugin_installations`, `mcp_servers`.
- **Governance:** `audit_logs`, `usage_events`.

## Vector storage
Embeddings are stored via pgvector with appropriate index types (e.g. HNSW/IVFFlat) chosen per
workload; see [`RAG_SYSTEM.md`](RAG_SYSTEM.md) and [`MEMORY_ENGINE.md`](MEMORY_ENGINE.md).

## Migrations
Forward-only, reversible where practical, versioned, and reviewed. No silent data loss
([`VERSIONING.md`](VERSIONING.md)). Every schema change ships with a migration and updated docs.

## Data protection
Encryption at rest for sensitive fields; least-privilege access; retention and deletion aligned
with [`SECURITY_POLICIES.md`](SECURITY_POLICIES.md) and privacy controls in
[`MEMORY_ENGINE.md`](MEMORY_ENGINE.md).
