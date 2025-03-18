# Chapter 08 - Monitoring & Logging and Error Management

## Observability
Observability helps in understanding a system’s behavior by collecting and analyzing data related to its operations. It consists of three main pillars:

### Monitoring
- Continuous tracking of system metrics like CPU usage, memory, response time, request rate, etc.
- Helps detect anomalies and performance issues.
- **Example:** Prometheus (metrics collection), Grafana (visualization).

### Logging
- Captures detailed event records that help diagnose problems.
- Logs can be structured (JSON) or unstructured (plain text).
- **Example:** ELK Stack (Elasticsearch, Logstash, Kibana) for log aggregation and analysis.

### Tracing
Tracks a request’s journey across multiple services (especially in microservices architecture).
Helps in debugging slow or failed requests.
Example: Jaeger, OpenTelemetry for distributed tracing.

## Monitoring Tools

### Prometheus
- Open-source monitoring tool that collects and stores time-series data.
- Pull-based system with powerful query language (PromQL).
- Works well with Grafana for visualization.
- 
### Grafana
- Visualization tool for monitoring metrics from Prometheus, InfluxDB, and more.
- Supports real-time dashboards and alerting.

### ELK Stack (Elasticsearch, Logstash, Kibana)
Elasticsearch: Stores and indexes logs for fast searching.
Logstash: Ingests, processes, and transforms logs.
Kibana: Provides UI for searching and analyzing logs.

## Fault Tolerance & Circuit Breaker Pattern

### Fault Tolerance
The system’s ability to continue functioning despite failures.
Achieved using redundancy, replication, retries, failover mechanisms.
Example: Load balancers, database replication, auto-scaling.

### Circuit Breaker Pattern
- Prevents cascading failures by stopping requests to a failing service.
- Works in three states
  1. Closed → Requests flow normally.
  2. Open → Requests are blocked after repeated failures.
  3. Half-Open → Allows limited requests to check if the service recovers.
Example: Netflix Hystrix, Resilience4j (for Java).
