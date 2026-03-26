# Stage233: External Signature Verification

## Overview

This stage introduces **external signature verification**.

Signatures are no longer purely internal.
They are now associated with **real-world identities**.

Example:

- self (owner)
- GitHub user
- external researcher

👉 This connects the system to **real-world trust**

---

## Concept

Previous stage:


Stage232: Threshold Signature
→ Structure only (2-of-3)


This stage:


Stage233: External Signatures
→ Real-world identities attached


---

## Why This Matters

- Moves from abstract model to real-world trust
- Enables identity-based validation
- Prepares for real cryptographic signatures
- Foundation for external verification and collaboration

---

## External Signers

Defined in:


external_signatures/config.yaml


Example:

```yaml
external_signers:
  - id: self
    type: local_key

  - id: github_user
    type: github_identity

  - id: researcher
    type: external_identity
How It Works

Verification logic:

Count valid signatures
↓
Check if threshold is met
↓
PASS / FAIL
Run
./tools/run_stage233_external.sh

Expected output:

[OK] External signatures verified
Structure
stage233/
├── external_signatures/
│   └── config.yaml
├── tools/
│   ├── verify_external_signatures.py
│   └── run_stage233_external.sh
Security Perspective

This stage introduces:

Identity-bound signatures
External trust anchors
Real-world validation model
Limitations
Signatures are simulated
No cryptographic verification yet
No key management
Next Stage

Stage234:

👉 Real cryptographic signatures

Ed25519
GPG / GitHub verified signatures
Actual key validation
License

MIT License

Copyright (c) 2025 Motohiro Suzuki