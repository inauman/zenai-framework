# Logging Standard

Logs are how you debug production issues, trace user journeys, and understand system behavior. Structured, consistent logging is not optional — it's infrastructure.

## Core Principles

### Structured Logging
- Use structured format (JSON or key-value) for automated processing
- Include consistent fields: timestamp, level, message, component, trace_id
- Human-readable messages with machine-parseable metadata
- Never use print statements in production code — use the logging framework

### Observability Triad
- **Logs**: What happened (discrete events)
- **Metrics**: How much/how often (aggregated measurements)
- **Traces**: The journey (request flow across components)

### End-to-End Traceability
- Unique trace ID for each user request
- Propagate trace context through all boundaries (HTTP headers, message queues)
- Link related operations with span IDs
- Support distributed tracing for multi-service architectures

## Log Levels

| Level | When | Example |
|---|---|---|
| **ERROR** | Something failed and needs attention | "Failed to broadcast transaction: timeout" |
| **WARN** | Something unexpected but handled | "Retry attempt 2/3 for relay connection" |
| **INFO** | Normal operation milestones | "Wallet synced: 150 transactions" |
| **DEBUG** | Detailed flow for troubleshooting | "PSBT created with 3 inputs, 2 outputs" |
| **TRACE** | Very detailed, usually disabled | "Entering function X with params Y" |

## Security in Logging

**CRITICAL**: Never log sensitive data.

| Data Type | Logging Rule |
|---|---|
| Private keys, seeds, mnemonics | NEVER log (Tier 1) |
| Public keys, addresses | Redact: show first/last 4 chars (Tier 2) |
| Transaction IDs, operation types | Safe to log (Tier 3) |
| Error messages | Sanitize — no internal paths, no stack traces to users |

Use redaction helpers:
```
# Instead of: log("sending to {}", address)
# Use:        log("sending to {}", redact(address))
# Output:     "sending to bc1q...3t4"
```

## Structured Log Format

```json
{
  "timestamp": "2025-03-28T14:30:00Z",
  "level": "INFO",
  "message": "Transaction broadcast successful",
  "component": "wallet.broadcast",
  "trace_id": "abc123",
  "txid": "e1234...abc",
  "fee_sats": 5500,
  "duration_ms": 230
}
```

## Anti-Patterns

- Print statements instead of structured logging
- Logging sensitive data "temporarily" for debugging
- No trace IDs (impossible to follow a request across components)
- Logging everything at INFO level (noise drowns signal)
- Not logging errors (silent failures)
- Logging in hot loops (performance impact)

## Performance Considerations

- Avoid expensive operations in log construction (format only if level is enabled)
- Use async logging for high-throughput paths
- Set appropriate default levels (INFO for production, DEBUG for development)
- Implement log rotation and size limits
