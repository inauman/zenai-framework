# Error Handling Standard

Errors are information, not failures. Good error handling turns problems into actionable guidance for both users and developers.

## Core Principles

### User-Centric Errors
- Clear, actionable messages — tell the user what went wrong and how to fix it
- No technical jargon in user-facing errors
- Graceful degradation — the system continues to function when possible
- Recovery guidance — specific steps, not vague "try again later"

### Developer-Friendly Errors
- Structured error information for debugging (error code, context, stack location)
- Context preservation through the call stack
- Error categorization for appropriate handling
- Traceability — link errors to specific code locations and user actions

### Security-Conscious Errors
- Never expose sensitive data in error messages (paths, keys, internal state)
- Sanitize errors before displaying to users
- Log security-relevant errors for investigation
- Don't leak implementation details through error messages

## Error Structure

A well-structured error includes:

```json
{
  "error": "Human-readable message",
  "code": "snake_case_error_code",
  "exit_code": 20,
  "suggestion": "How to fix this",
  "retryable": false
}
```

| Field | Purpose |
|---|---|
| `error` | What went wrong (human-readable) |
| `code` | Machine-parseable identifier (for scripts/agents) |
| `exit_code` | Process exit code (for shell-level handling) |
| `suggestion` | How to resolve (actionable) |
| `retryable` | Whether retry makes sense (for automation) |

## Error Categories

| Category | Example | Handling |
|---|---|---|
| **Validation** | Invalid input, missing fields | Reject immediately with guidance |
| **Authentication** | Expired token, wrong credentials | Prompt re-authentication |
| **Authorization** | Insufficient permissions | Explain what's needed |
| **Not Found** | Missing resource | Suggest creation or check |
| **Conflict** | Duplicate, race condition | Explain current state |
| **External** | Network timeout, service down | Retry with backoff |
| **Internal** | Bug, unexpected state | Log details, show generic message |

## Error Handling Patterns

### Fail Fast
Detect errors at the boundary and reject early. Don't propagate invalid state deep into the system.

### Error Propagation
Use the language's error handling idioms (Result/Option in Rust, try/catch in JavaScript). Don't swallow errors silently.

### Retry with Backoff
For transient failures (network, external services):
- Retry 2-3 times with exponential backoff
- Mark the error as `retryable: true` for automation
- Give up after max retries with a clear error

### Circuit Breaker
For dependencies that are down:
- After N consecutive failures, stop trying (circuit opens)
- Periodically check if the dependency recovered (half-open)
- Resume normal operation when recovered (circuit closes)

## Anti-Patterns

- **Swallowed errors**: Catching exceptions and doing nothing (`catch {}`)
- **Generic messages**: "An error occurred" (tells user nothing)
- **Stack traces to users**: Exposing internal implementation
- **Panic in library code**: Use Result/Error types, let the caller decide
- **Stringly-typed errors**: Plain strings instead of typed error enums
- **Inconsistent error formats**: Different shapes from different endpoints

## Exit Codes (CLI Applications)

Group exit codes by domain for shell-level pattern matching:

| Range | Domain | Examples |
|---|---|---|
| 0 | Success | — |
| 1 | Usage | Invalid args, missing flags |
| 10-19 | Server/Network | Unreachable, auth, server error |
| 20-29 | Resource | Not found, conflict, validation |
| 30-39 | Crypto/Signing | Key error, signing failure |
| 40-49 | External | Relay, third-party service |
| 70-79 | System | Internal error, config error |

Reserve codes 2 (bash), 64-78 (deprecated sysexits), 126-127 (shell), 128+ (signals).
