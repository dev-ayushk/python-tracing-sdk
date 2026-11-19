# Architecture

_To be written before the first line of core code: what a trace and a span are, how the active span is tracked, and how spans reach exporters. Add the hand-drawn diagram here._

## Open design questions

- Is a separate `Trace` object needed, or is a trace just the set of spans that share a `trace_id`?
