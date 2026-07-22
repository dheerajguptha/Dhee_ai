# Observability

```
Status: Draft
Priority: High
Owner: Repository Maintainer
Depends On: ENGINEERING_CONSTITUTION.md, ARCHITECTURE.md, ERROR_STANDARDS.md
Related Documents: SECURITY_POLICIES.md, AGENT_RUNTIME.md, DEPLOYMENT.md
Next Expansion: Define the metrics catalog, tracing spans, and audit-log schema.
Last Updated: 2026-07-23
```

## Purpose
Make the system understandable in production through logs, metrics, traces, and audit records.

## Scope
Structured logging, metrics, distributed tracing, audit logging, and alerting.

## Design intent
- **Logging:** structured JSON with `requestId`, severity, and context; never logs secrets or
  sensitive prompt data ([`ERROR_STANDARDS.md`](ERROR_STANDARDS.md)).
- **Metrics & tracing:** OpenTelemetry across services ([`TECH_STACK.md`](TECH_STACK.md));
  latency, throughput, error rate, and cost/token metrics for AI operations.
- **Audit logs:** security- and governance-relevant events (auth decisions, agent actions,
  admin changes) are recorded immutably ([`SECURITY_POLICIES.md`](SECURITY_POLICIES.md)).
- **Agent transparency:** every agent run/step is observable for review
  ([`AGENT_RUNTIME.md`](AGENT_RUNTIME.md)).

## Alerting
Actionable alerts on SLO breaches and error spikes; dashboards for health and cost. Retention and
access follow privacy and security policies.
