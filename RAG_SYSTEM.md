# RAG System

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, MEMORY_ENGINE.md, AI_PROVIDER_LAYER.md
Related Documents: DATABASE_SCHEMA.md, EDITOR_ENGINE.md, FILESYSTEM_ENGINE.md
Next Expansion: Define ingestion pipeline, chunking strategies, and retrieval/reranking config.
Last Updated: 2026-07-23
```

## Purpose
Provide retrieval-augmented generation so the system can ground responses in documents, code,
and memory.

## Scope
Ingestion, chunking, embeddings, indexing, retrieval, reranking, and repository-scale
understanding.

## Pipeline (design intent)
1. **Ingest** documents/code/attachments from workspaces and uploads.
2. **Chunk** with strategy-appropriate boundaries (semantic, structural, code-aware).
3. **Embed** via the provider layer ([`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md)).
4. **Index** in pgvector ([`DATABASE_SCHEMA.md`](DATABASE_SCHEMA.md)).
5. **Retrieve** top-k with filters; **rerank** for relevance.
6. **Augment** the prompt via the context manager within token budgets.

## Repository understanding
Code-aware indexing (symbols, structure, dependencies) powers repository-scale reasoning for the
IDE and agents ([`EDITOR_ENGINE.md`](EDITOR_ENGINE.md), [`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).

## Quality & evaluation
Retrieval quality is measured and tuned; citations/traceability are preserved so answers can be
grounded and audited.

## Privacy & security
Respects tenant isolation and privacy controls ([`MEMORY_ENGINE.md`](MEMORY_ENGINE.md),
[`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)); no cross-tenant retrieval.
