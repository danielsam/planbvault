# Plan B Vault – Master Project Specification

**Version 1.0 – May 2025**
**High-Level Design, Modular Breakdown, and Interface Contracts**
**Website:** [planbvault.com](https://planbvault.com)
**Contact:** [hello@planbvault.com](mailto:hello@planbvault.com)

---

## 1. Project Overview

* **Vision**: Enable sovereign, encrypted inheritance and dead man’s switch functionality without custodial trust.
* **Target Users**: Bitcoiners, journalists, estate planners, whistleblowers.
* **Core Principles**: Privacy, sovereignty, decentralization, zero-trust, client-side encryption.
* **Use Cases**:

  * Bitcoin inheritance
  * Dead man’s switch for document release
  * Whistleblower protection
  * Secure posthumous messaging

---

## 2. System Architecture

**Key Components:**

* Vault Creator UI (Frontend)
* Encryption Engine (client-side)
* Trigger Logic Layer (check-in, guardians, time-locks)
* Guardian Coordination
* Vault Storage (user or optionally hosted)
* Key Reconstruction and Release
* Admin Panel for billing/relay

---

## 3. Modular Breakdown

Each module is designed to be implemented in a dedicated chat/thread.

| Module ID | Name              | Role                                       |
| --------- | ----------------- | ------------------------------------------ |
| 01        | Vault Creator UI  | Frontend form + vault export               |
| 02        | Vault Unlocker UI | Decryption & recovery UI                   |
| 03        | Encryption Engine | AES-GCM, Shamir logic, format definition   |
| 04        | Trigger System    | Inactivity, time-lock, guardian quorum     |
| 05        | Guardian Module   | Quorum signature gathering, authentication |
| 06        | Key Management    | Reconstruction from Shamir or guardians    |
| 07        | Vault Storage     | Optional file hosting via S3/IPFS/Arweave  |
| 08        | Admin Panel       | Relay mgmt, billing, unlock logs           |
| 09        | Testing & QA      | Unit, integration, fuzzing plan            |
| 10        | Protocol Docs     | Open spec, .vault schema, guides           |

---

## 4. Development Phases

**Q2 2025:** MVP – vault creation, encryption, trigger simulator, unlocker UI

**Q3 2025:** Full trigger logic, guardian flows, LNURL/Nostr check-in integration

**Q4 2025:** SDK release, open spec, relay deployment, offline unlock kits

---

## 5. Assigned Roles & Chat Threads

Each chat is assigned to act as one of the following roles:

* UI Designer – vault creator/unlocker UI
* Cryptographer – encryption + Shamir implementation
* Backend Developer – trigger daemon
* Coordinator – guardian flow/threshold logic
* QA Lead – test specs + automation
* Doc Lead – .vault format + event schema
* Relay Engineer – storage API + unlock backend

---

## 6. Interface Contracts

### .vault File Format v1.0

JSON file containing:

* version
* created\_at
* recipient (email, pubkey)
* trigger (type, parameters)
* payload (ciphertext, nonce, auth\_tag)
* optional: shamir\_shares, guardian\_ids

### Encryption

* AES-256-GCM (WebCrypto)
* Random key `K`
* Nonce: 12 bytes
* Auth tag: 16 bytes

### Guardian Signature Format

```json
{
  "vault_id": "abc123",
  "guardian_pubkey": "npub...",
  "sig": "hex...",
  "timestamp": 1682827200
}
```

### Trigger Event Format

```json
{
  "vault_id": "abc123",
  "trigger": "time_lock_expired",
  "unlock_at": "2025-06-01T00:00:00Z"
}
```

### Decryption API

* Input: `.vault` + `key K`
* Output: Plaintext message/files
* Errors: Invalid key, tampered payload, auth tag fail

---

## 7. Versioning Rules

* Modules and vault format versioned `vMAJOR.MINOR.PATCH`
* Changes to `.vault` schema bump MINOR if compatible, MAJOR if breaking
* Compatibility matrix must be maintained between creator and unlocker

---

## 8. Testing Strategy

* Unit tests for each module (encryption, UI, trigger)
* End-to-end integration test: create → trigger → release → decrypt
* Fuzzing for malformed files
* Simulated edge cases: multiple triggers, corrupted shares, missed check-ins

---

## 9. Deployment Strategy

* MVP: Hosted on GoDaddy (planbvault.com)
* Vaults downloaded locally or stored on S3/IPFS
* Future: user-runnable PWA, Arweave/Pinata plugin

---

## 10. Governance and Licensing

* Open source repository on GitHub (MIT or AGPL license TBD)
* Community contribution roadmap
* PGP-signed versions + checksums for vault unlocker

---
