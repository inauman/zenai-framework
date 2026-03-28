# Security Standard

Treat every project as potentially handling sensitive or high-risk data. Security is a default posture, not an add-on phase.

## Security-First Mentality

- Assume adversarial environments
- Prefer audited tools and minimal surface area
- Avoid storing or exposing secrets unnecessarily
- Validate inputs, outputs, and storage decisions

## Key Practices

### Memory Safety
- Wipe sensitive variables from memory after use (e.g., `zeroize` in Rust, `crypto.timingSafeEqual` in Node.js)
- Avoid storing passphrases, seeds, or keys in memory longer than necessary
- Never log or stringify sensitive content
- Classify data: Tier 1 (never log), Tier 2 (redact), Tier 3 (safe)

### Secure Defaults
- Encryption at rest for sensitive data
- TLS for all network communication
- Private by default (fields, methods, modules)
- Fail secure, not fail open

### Platform-Specific Storage
- Use OS credential stores (Keychain, Secret Service, Windows Credential Manager)
- File permissions (0600 for secrets, 0700 for directories)
- Never store secrets in environment variables, config files, or code

### Input Validation
- Validate at system boundaries (user input, API requests, external data)
- Reject invalid input early (fail fast)
- Sanitize output (prevent injection: SQL, command, XSS)
- Validate amounts, addresses, and identifiers before operations

### Dependency Security
- Audit dependencies regularly (`cargo audit`, `npm audit`)
- Minimize dependency count (each is an attack surface)
- Pin versions for reproducible builds
- Review dependency updates before adopting

### Threat Modeling
- Identify assets (what are we protecting?)
- Identify threats (who would attack? how?)
- Implement mitigations (specific defenses for each threat)
- Verify mitigations (test that they actually work)

## Secret Classification

| Tier | Examples | Rule |
|---|---|---|
| **Tier 1 (Never)** | Private keys, seeds, mnemonics, passwords | Never log, never in output, never in version control |
| **Tier 2 (Redact)** | Public keys, addresses, tokens | Show first/last 4 chars only |
| **Tier 3 (Safe)** | Transaction IDs, operation types, timestamps | Log freely |

## Anti-Patterns

- Storing secrets in plaintext config files
- Logging sensitive data "for debugging"
- Security through obscurity (hiding code instead of encrypting data)
- Trusting client-side validation alone
- Using custom cryptography instead of established libraries

## Integration

Consider creating a domain skill (e.g., `/d-security`) if your project has specialized security requirements (cryptographic protocols, hardware security, financial compliance). This standard provides the foundation — domain skills provide the depth.
