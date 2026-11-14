# IAOP Grafana Dashboards

Dashboard JSON files for the IAOP platform live here (`*.json`,
importable via Grafana → Dashboards → Import).

## Planned dashboards

- **IAOP Service Overview** — RED metrics (rate/errors/duration) per
  service, sourced from OTel metrics via Prometheus.
- **IAOP Events & Outbox** — outbox backlog depth, publish latency,
  inbox dedup rejections.
- **IAOP Workflow** — Flowable process instance counts, task aging.

Until service metrics endpoints are enabled, the collector's Prometheus
exporter (`:8889`) exposes infra-level metrics only.
