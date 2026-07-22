# Git Engine

```
Status: Draft
Priority: Medium
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, SECURITY_MODEL.md
Related Documents: FILESYSTEM_ENGINE.md, EDITOR_ENGINE.md, AGENT_RUNTIME.md, NAMING.md
Next Expansion: Define the git operation API, diff model, and AI commit/PR assistance.
Last Updated: 2026-07-23
```

## Purpose
Provide version control operations in the IDE and to agents, with a rich diff experience and AI
assistance.

## Scope
Status, stage, commit, branch, merge, diff, history, and remote operations, plus AI-generated
commit messages and PR summaries.

## Design intent
- **Operations:** a typed git API over the workspace ([`FILESYSTEM_ENGINE.md`](FILESYSTEM_ENGINE.md)).
- **Diff viewer:** side-by-side and inline diffs shared with the editor
  ([`EDITOR_ENGINE.md`](EDITOR_ENGINE.md)).
- **AI assistance:** commit messages and PR summaries follow Conventional Commits
  ([`NAMING.md`](NAMING.md)); destructive operations require Human Override
  ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).

## Security
Credentials handled as secrets ([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)); no force-push
or history rewrite without explicit user confirmation.
