Stage221 – Independent Verification Kit

QSP Transparency System – Reproducible Verification

Stage221 introduces an independent verification kit that allows third parties to reproduce and verify the transparency log and Merkle commitments.

This stage moves the project from:

Anyone can audit
→
Anyone can reproduce

The verification process rebuilds the transparency log, validates the Merkle tree, checks checkpoint history, and runs an external monitoring tool.

This approach aligns with the core principles of:

Certificate Transparency

Supply Chain Transparency

Reproducible Security Research

Overview

The transparency system records evidence artifacts and binds them to a Merkle commitment.

Artifacts include:

CI run evidence

security test logs

monitoring reports

These artifacts are committed to a Merkle tree, producing a verifiable root hash.

Checkpoint history ensures the log evolves in an append-only manner.

Stage Evolution
Stage	Feature
Stage218	Transparency checkpoint generation
Stage219	Checkpoint history (append-only log)
Stage220	External transparency monitor
Stage221	Independent verification kit

Stage221 enables complete third-party verification.

Repository Structure
tools/
 ├─ build_transparency_log.py
 ├─ verify_transparency_log.py
 ├─ external_monitor.py
 ├─ archive_checkpoint.py
 └─ verify_all.sh

out/
 ├─ transparency/
 │   ├─ transparency_log.json
 │   ├─ merkle_tree.json
 │   ├─ root.txt
 │   ├─ checkpoint.json
 │   ├─ history/
 │   │   └─ checkpoint_0001.json
 │   └─ inclusion_proofs/
 │
 ├─ ci/
 ├─ logs/
 └─ monitor/
Independent Verification

The full verification pipeline can be executed with a single command.

./tools/verify_all.sh

This script performs the following steps:

Rebuild transparency log

Archive checkpoint to history

Verify Merkle tree integrity

Verify checkpoint history

Run external monitor

Example Output
[1] rebuild transparency log
[OK] wrote: out/transparency/transparency_log.json

[2] archive current checkpoint into history
[OK] archived checkpoint: out/transparency/history/checkpoint_0001.json

[3] verify transparency log + Merkle tree + checkpoint history
[OK] transparency log + Merkle tree verified
[OK] checkpoint history verified

[4] run external monitor
[OK] external monitor completed

[OK] independent verification completed
Security Properties
Integrity

Evidence artifacts cannot be modified without changing the Merkle root.

Transparency

All entries are publicly auditable.

Append-Only History

Checkpoint history ensures that previous states cannot be altered.

Independent Verification

Anyone can reproduce the verification process using verify_all.sh.

Research Significance

This stage demonstrates a reproducible transparency framework similar to modern transparency systems used in:

certificate ecosystems

supply-chain security

reproducible research infrastructure

The goal is to reduce ambiguity between:

Security Claims
↓
Evidence Artifacts
↓
Merkle Commitments
↓
Independent Verification
License

MIT License

Copyright (c) 2025 Motohiro Suzuki

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction.

Author

Motohiro Suzuki

GitHub
https://github.com/mokkunsuzuki-code