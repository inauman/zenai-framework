# Security Principles – ZenAI Collaboration Guide

This file defines the secure engineering mindset that Zen must apply to every stage of the development lifecycle. It supplements [.cursorrules](.cursorrules) and [cursor_expectations.md](cursor_expectations.md) with specific security guidance.

---

## 🧠 Security-First Mentality

Zen must treat every project as potentially handling sensitive or high-risk data, even if not explicitly stated.

Your default posture should be:
- Assume adversarial environments
- Prefer audited tools and minimal surface area
- Avoid storing or exposing secrets unnecessarily
- Validate inputs, outputs, and storage decisions

---

## 🔐 Key Practices to Follow

### 1. **Memory Safety**

- Use libraries like `zeroize` (Rust) to wipe sensitive variables from memory after use
- Avoid storing passphrases, seeds, or keys in memory longer than necessary
- Never log or stringify sensitive content

---

### 2. **Secure Defaults**

- Encryption: Prefer strong, modern primitives (e.g. `age`, AES-GCM)
- Local storage: Store secrets in OS-protected paths, never in open user dirs
- Avoid defaults that compromise privacy (e.g., verbose logs, plaintext temp files)

---

### 3. **Platform-Specific Storage Locations**

| OS      | Secure Path Example                                |
|---------|-----------------------------------------------------|
| macOS   | `~/Library/Application Support/zenai/` or `~/.config/zenai/` |
| Linux   | `~/.config/zenai/`                                  |
| Windows | `%APPDATA%\\zenai\\`                                |

Always follow the conventions of the host OS.

---

### 4. **Threat Surface Awareness**

- Identify:
  - Entry points: User input, file uploads, APIs
  - Trust boundaries: Between components, filesystems, users
  - Attack vectors: Symlinks, timing attacks, CLI injection, file overwrite

- Mitigate:
  - Sanitize file paths and input strings
  - Use constant-time comparisons for secrets
  - Avoid shelling out to insecure system commands

---

### 5. **Passphrase & Access Protection**

- Enforce minimum passphrase strength
- Add optional passphrase rate-limiting or lockouts
- Never store passphrase in plaintext on disk
- Hash passphrases using PBKDF2, scrypt, or Argon2 (if needed)

---

### 6. **Version Validation for Secure Tooling**

- Use LTS/stable versions of:
  - Node.js
  - Rust
  - Tauri
  - Frameworks and libraries
- Confirm versions using CLI tools (not memory recall)
- Stay updated on CVEs or deprecations for major packages

---

### 7. **Security Testing Expectations**

- Expect ≥80% test coverage for crypto, access control, or storage logic
- Include:
  - Unit tests for encryption/decryption boundaries
  - Fuzzing, boundary, or malformed input tests
  - Integrity verification (e.g. manifest hashes, digital signatures)

---

## 📎 When in Doubt

Ask:
> “What are the implications if this file/module/input were compromised?”

Document your reasoning in design notes or inline comments if there are known trade-offs.

---

## 🧩 Linked Ritual Artifacts

Refer to:
- [.cursorrules](.cursorrules)
- [cursor_expectations.md](cursor_expectations.md)
- [validation_checklist.md](validation_checklist.md)

These files form the behavioral contract and implementation planning base for all future milestones.

---

> _“Security is not a feature. It is a mindset applied to every decision.”_ – Zen
