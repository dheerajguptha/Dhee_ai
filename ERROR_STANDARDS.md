# Error Handling Standards

```
Status: Stable
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, PRINCIPLES.md, NAMING.md
Related Documents: API_SPEC.md, AI_PROVIDER_LAYER.md, AUTH_SYSTEM.md, DATABASE_SCHEMA.md, OBSERVABILITY.md
Next Expansion: Publish the full canonical error-code registry as errors are implemented.
Last Updated: 2026-07-23
```

This document defines the universal error model for Dhee_AI. It applies to every service,
package, SDK, and agent. Errors are explicit, typed, and actionable (principles: Explicit Over
Implicit, Secure by Default).

## Error object shape
Every error surfaced across a boundary is normalized to a stable structure:

```jsonc
{
  "code": "AUTH.TOKEN_EXPIRED",      // stable, machine-readable
  "message": "Your session has expired. Please sign in again.", // user-friendly
  "detail": "JWT exp=... now=...",   // internal diagnostic (never shown to end users)
  "httpStatus": 401,                  // when applicable
  "retryable": false,
  "requestId": "req_...",            // correlation id for tracing
  "cause": { }                        // optional nested/original error
}
```

- Public/user-facing responses expose `code`, `message`, `httpStatus`, `retryable`,
  `requestId`. `detail` and `cause` are for logs/diagnostics only and must never leak secrets.

## Error code taxonomy
Codes are `DOMAIN.REASON` in `UPPER_SNAKE_CASE`. Domains:

- `AUTH` — authentication (identity).
- `AUTHZ` — authorization (permissions).
- `VALIDATION` — malformed or invalid input.
- `PROVIDER` — AI provider layer failures.
- `DB` — database/persistence failures.
- `NETWORK` — connectivity/timeout failures.
- `RATE_LIMIT` — throttling/quota.
- `CONFLICT` — state conflicts (e.g., version mismatch).
- `NOT_FOUND` — missing resource.
- `INTERNAL` — unexpected server faults.
- `PLUGIN` / `MCP` — extension/tooling failures.

## Category standards

### API errors
- Map to appropriate HTTP status (`400/401/403/404/409/422/429/5xx`).
- Always include `code`, `message`, `requestId`. Batch/validation errors include a `fields`
  array. See [`API_SPEC.md`](API_SPEC.md).

### AI provider errors
- Normalize provider-specific errors into `PROVIDER.*` (e.g. `PROVIDER.RATE_LIMITED`,
  `PROVIDER.CONTEXT_LENGTH_EXCEEDED`, `PROVIDER.CONTENT_FILTERED`, `PROVIDER.UNAVAILABLE`).
- Preserve the original provider error in `detail`/`cause` for diagnostics.
- Support failover/routing per [`AI_PROVIDER_LAYER.md`](AI_PROVIDER_LAYER.md).

### Validation errors
- `VALIDATION.*` with a `fields` array: `{ path, code, message }`. Validate at boundaries with
  schemas; never trust external input.

### Authentication errors (`AUTH.*`)
- `AUTH.INVALID_CREDENTIALS`, `AUTH.TOKEN_EXPIRED`, `AUTH.MFA_REQUIRED`. Never reveal whether
  an account exists (avoid user enumeration).

### Authorization errors (`AUTHZ.*`)
- `AUTHZ.FORBIDDEN`, `AUTHZ.INSUFFICIENT_SCOPE`. Deny by default; do not leak resource
  existence to unauthorized callers.

### Database errors (`DB.*`)
- `DB.UNAVAILABLE`, `DB.CONSTRAINT_VIOLATION`, `DB.SERIALIZATION_FAILURE`. Wrap driver errors;
  never surface raw SQL to clients.

### Network errors (`NETWORK.*`)
- `NETWORK.TIMEOUT`, `NETWORK.DNS`, `NETWORK.CONNECTION_RESET`. Generally `retryable: true`.

## Retry policies
- Retry only idempotent operations or those with an idempotency key.
- Use exponential backoff with jitter; cap attempts (default: 3) and total time.
- Respect `Retry-After` and provider rate-limit headers.
- Circuit-break on repeated failures to a dependency; fail fast while open.

## Recovery strategies
- **Failover:** switch AI provider/model when one is unavailable.
- **Graceful degradation:** reduce functionality rather than fail entirely (e.g., disable
  streaming, shrink context).
- **Compensation:** for multi-step workflows, define compensating actions to undo partial work.

## Logging standards
- Structured JSON logs with `requestId`, `code`, `severity`, and context. See
  [`OBSERVABILITY.md`](OBSERVABILITY.md).
- Log `detail`/`cause` server-side only. **Never log secrets, tokens, or full prompts
  containing sensitive data.**
- Severity: `debug < info < warn < error < fatal`.

## Messaging
- **User-friendly messages:** clear, non-technical, actionable, no stack traces or internal
  identifiers.
- **Internal diagnostic messages:** precise, include correlation ids and causes, intended for
  operators and logs.
