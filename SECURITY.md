# Security Policy

## Reporting a Vulnerability

If you discover a vulnerability in Plan B Vault, please report it responsibly.

- Email: [security@planbvault.com](mailto:security@planbvault.com)
- Optional PGP Key: [Coming Soon – all critical disclosures will be signed]

Please include:
- A description of the issue
- Steps to reproduce (if possible)
- Your contact information and public key (if available)

We strongly encourage encrypted communication when reporting sensitive findings.

---

## Disclosure Policy

We follow a coordinated disclosure model:

- We will acknowledge your report within 72 hours
- We will assess, validate, and respond to the issue
- If it is critical, we will prepare a patch within 7–14 days
- You will be credited (with permission) in the changelog upon resolution

---

## Scope

This project deals with sensitive cryptographic operations and secure messaging. We welcome reports involving:

- Client-side encryption vulnerabilities
- Key reconstruction flaws
- Trigger manipulation
- Guardian impersonation
- Vault format integrity
- Privilege escalation in relay or admin systems

---

## Out of Scope

While important, the following are generally considered out of scope unless they lead to a direct exploit:

- DoS attacks that require full user interaction
- Lack of rate limiting on non-critical endpoints
- User error in storing/downloaded files

---

## Our Security Commitments

- All cryptographic functions will use well-established libraries (e.g. WebCrypto, libsodium)
- Code affecting encryption or decryption will be documented, peer-reviewed, and test-covered
- Vault specs and releases will be PGP-signed and checksummed
- We will never collect unencrypted user vault content

---

## Security Philosophy

Plan B Vault is built around the principles of:
- User sovereignty
- Zero trust
- Local encryption
- Decentralized key handling

Security is not a layer — it's the foundation. All designs are made assuming hostile environments and intent to minimize any single point of failure.

