# python-tracing-sdk

A lightweight Python tracing SDK built from first principles to understand how tracing works inside: span lifecycle, parent-child relationships, context propagation with `contextvars`, async and thread safety, and pluggable exporters.

> **Status:** early development. Nothing is usable yet.

This is a learning project, not a replacement for [OpenTelemetry](https://opentelemetry.io/). For production tracing, use OpenTelemetry.

## Intended API

```python
with tracer.start_as_current_span("generate_report") as span:
    span.set_attribute("report.type", "monthly")
    with tracer.start_as_current_span("fetch_data"):
        data = fetch_data()


@tracer.trace("fetch_customer_data")
async def fetch_customer_data(customer_id: str) -> dict:
    ...
```

## Roadmap

- [ ] **M1 — Sync core:** span model and lifecycle, `contextvars`-based context, context manager and decorator (including generators), in-memory exporter.
- [ ] **M2 — Async and concurrency:** async support, `gather` / `TaskGroup`, cancellation, threads, batch exporter with bounded queue, failure isolation.
- [ ] **M3 — Integrations:** FastAPI middleware, W3C `traceparent` propagation, overhead benchmark.

## Development

Requires Python 3.11+ and [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run pytest
uv run mypy
uv run ruff check . && uv run ruff format --check .
```

## License

MIT
