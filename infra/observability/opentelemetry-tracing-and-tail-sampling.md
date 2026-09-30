# Why 100% Distributed Tracing Is an Operational Bottleneck

## The Storage Cost Trap of Naive Tracing
Emitting OpenTelemetry traces for 100% of HTTP requests in a high-traffic microservices architecture is a silent compute and financial drain.
- 99% of those traces represent boring 200 OK healthchecks and fast static queries that no engineer ever looks at.
- Ingestion costs in Datadog or Grafana Tempo scale linearly with request volume, quickly eclipsing your primary database hosting bills.

## Tail-Based Sampling Over Head-Based Sampling
Do not make sampling decisions at the load balancer or when the request begins (head sampling).
- With head sampling, if you sample 5% of traffic, you will inevitably drop 95% of your 500 Internal Server Errors and p99 latency spikes.
- Use Tail-Based Sampling in an OpenTelemetry Collector gateway. Keep traces in a temporary 30-second in-memory ring buffer.
- Route traces to long-term storage strictly if:
  1. HTTP status code is >= 400.
  2. Total trace duration exceeds 800ms.
  3. Explicit debug headers (`x-debug-trace: true`) are present.
- This dropped our telemetry ingestion volume by 82% while retaining 100% of actionable production anomalies.
