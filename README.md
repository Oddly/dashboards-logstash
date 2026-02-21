# Logstash Dashboards for Grafana

> **Work in progress.** These dashboards are under active development. Layouts, panel queries, and field references may change without notice.

Grafana dashboards for monitoring Logstash nodes and pipelines. Designed for use with an Elasticsearch backend datasource and data collected by standard Elastic Agent integrations (Fleet-managed).

## Dashboards

| ID | Title | Description |
|---|---|---|
| LS-00 | Service Overview | Node health, event throughput, pipeline summary |
| LS-01 | Pipeline Metrics | Per-pipeline throughput, flow rates, queue backpressure |
| LS-02 | Pipeline Detail | Single pipeline breakdown with filter and output timing |
| LS-03 | Node Performance | JVM heap, GC, process CPU, file descriptors |
| LS-04 | Pipeline Tuning | Worker utilization, batch sizes, queue saturation |
| LS-09 | Host Metrics | CPU, memory, disk, network for Logstash hosts |

## Data Sources

These dashboards use template variables for datasource selection, so they work with any Elasticsearch datasource name or UID. The expected data comes from:

- **Elastic Agent** `logstash` integration (pipeline and node metrics)
- **Elastic Agent** `system` integration (host-level metrics for LS-09)

Some dashboards also use the [Infinity datasource](https://grafana.com/grafana/plugins/yesoreyeram-infinity-datasource/) to query the Logstash monitoring API directly for node stats and pipeline configuration not available through the metrics pipeline. These panels are optional — dashboards work without them but will show empty panels where Infinity is not configured.

## Installation

Copy the JSON files from `dashboards/` into Grafana via the UI import, the HTTP API, or the [grafana-dashboards-role](https://github.com/Oddly/grafana-dashboards-role) Ansible role.
