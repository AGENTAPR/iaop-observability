# iaop-observability

Metrics, logs, tracing, dashboards, alerts.

## Purpose

iaop-observability is part of the **Insurance Agent Operating Platform (IAOP)**, an enterprise
insurance agent lifecycle platform.

## Bounded Context / Ownership

- **Bounded context:** Observability
- **Owner:** AGENTAPR
- **Group:** infrastructure

## Owned Database

N/A (no owned database)

Each service owns its persistence. No cross-service database access, no shared domain
entities, and no cross-database foreign keys.

## Technical Stack

OpenTelemetry, Prometheus, Grafana, Loki/ELK

## Architecture Principles

- Domain-Driven Design (DDD) with explicit bounded contexts
- Hexagonal architecture (ports and adapters)
- Event-driven integration via versioned contracts (see iaop-event-contracts)
- Transactional outbox/inbox for reliable event publication
- PostgreSQL as the system of record where applicable
- Identity and access via Keycloak
- Workflow orchestration via Flowable BPM (see iaop-workflow-service)
- Observability via OpenTelemetry

## Responsibilities

- Metrics collection config
- Distributed tracing setup
- Dashboards
- Alert rules

## Non-Responsibilities

- Application instrumentation code (per service)
- Infrastructure provisioning

## Integration

### Upstream (callers / producers toward this service)

- (none)

### Downstream (services this depends on)

- `All services`

### Planned Integration Events

- (none planned yet)

Event schemas are governed by [iaop-event-contracts](https://github.com/AGENTAPR/iaop-event-contracts).

### Planned API Contracts

- (none yet)

API specifications are governed by [iaop-api-contracts](https://github.com/AGENTAPR/iaop-api-contracts).

## Related Repositories

- [iaop-architecture](https://github.com/AGENTAPR/iaop-architecture) - DDD strategic design, bounded context maps, ADRs, repository landscape
- [iaop-rust-common](https://github.com/AGENTAPR/iaop-rust-common) - Shared Rust technical utilities
- [iaop-test-kit](https://github.com/AGENTAPR/iaop-test-kit) - Shared test infrastructure

## Status

**INITIALIZED - NOT IMPLEMENTED**

This repository has been bootstrapped with baseline documentation and configuration only.
No business logic or service implementation exists yet.

## Development Conventions

- Default branch: `main`
- Development branch: `development` — all changes are committed and pushed here
- Squash merges preferred; merge commits and rebases disabled
- Pull requests required before merging into `main`
- Topics: iaop, insurance, insurance-agents, enterprise-architecture, devops, observability, opentelemetry, prometheus, grafana, monitoring
## Foundation contents

- `otel-collector-config.yaml` — OTLP receiver → Prometheus exporter + debug exporter (used by `iaop-local-dev` compose profile `observability`)
- `prometheus.yml` — example scrape config for service `/metrics` endpoints
- `alerts/iaop-alerts.yml` — starting alert rules (availability, error rate, readiness)
- `dashboards/` — Grafana dashboard JSON (planned; see dashboards/README.md)
