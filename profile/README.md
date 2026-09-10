# 0x307

Open-source post-quantum cryptography for Rust and WASM: identity, signing, key exchange, and an agent-held wallet. Everything here is Apache-2.0 and published on crates.io.

## Identity

| Crate | What it does |
|---|---|
| [`aethel-core`](https://github.com/0x307/aethel-core) · [crates.io](https://crates.io/crates/aethel-core) | Post-quantum anonymous identity: per-context identifiers, zero-knowledge selective disclosure, context-bound ML-DSA signing. Ships a WebAssembly component. |
| [`aethel-sdk`](https://github.com/0x307/aethel-sdk) · [crates.io](https://crates.io/crates/aethel-sdk) | Ergonomic Rust SDK over aethel-core: generate, sign, verify, project, disclose, recover. |
| [`aethel-vault`](https://github.com/0x307/aethel-runtime) · [crates.io](https://crates.io/crates/aethel-vault) | Agent-held wallet. Policy-gated EIP-3009/x402 USDC signing with ML-DSA-65 spend intents and receipts; optional FHE confidential ledger. |

## Primitives

| Crate | What it does |
|---|---|
| [`pqc-sig`](https://github.com/0x307/pqc-sig) · [crates.io](https://crates.io/crates/pqc-sig) | ML-DSA (FIPS 204), SLH-DSA (FIPS 205), FN-DSA (FIPS 206) signatures. Standalone, WASM-compatible. |
| [`pqc-kem`](https://github.com/0x307/pqc-kem) · [crates.io](https://crates.io/crates/pqc-kem) | ML-KEM (FIPS 203) and hybrid X25519+ML-KEM-768 key encapsulation. Standalone, WASM-compatible. |
| [`pqc-privacy`](https://github.com/0x307/pqc-privacy) · [crates.io](https://crates.io/crates/pqc-privacy) | ML-KEM/ML-DSA key exchange and signing, AES-GCM encryption, erasure-coded sharding, plus clearly labeled experimental privacy primitives. |

## Networking

| Crate | What it does |
|---|---|
| [`witan`](https://github.com/0x307/witan-gossip) · [crates.io](https://crates.io/crates/witan) | Post-quantum gossip protocol runtime, built as a WebAssembly component. |

Each repository's README states what is production-grade and what is experimental. Security reports: see each repo's `SECURITY.md`.
