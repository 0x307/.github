# 0x307

**0x307 publishes the post-quantum primitives it builds its own products on.** FIPS 203, 204
and 205 in pure Rust, `no_std` and WASM-ready, with the test vectors and the unfinished parts
both in public.

Start with [`aethel-sdk`](https://github.com/0x307/aethel-sdk#quickstart), or run
[the examples](https://github.com/0x307/examples): one program per crate, pinned to the
published versions. Overview, tiers and licenses: [0x307.com/crates](https://0x307.com/crates).

## The crates

| Crate | Tier | What it does | License |
|---|---|---|---|
| [`pqc-sig`](https://github.com/0x307/pqc-sig) · [crates.io](https://crates.io/crates/pqc-sig) | Production | ML-DSA, SLH-DSA and FN-DSA signatures (FIPS 204/205/206) | MIT OR Apache-2.0 |
| [`pqc-kem`](https://github.com/0x307/pqc-kem) · [crates.io](https://crates.io/crates/pqc-kem) | Production | ML-KEM (FIPS 203), the X25519 + ML-KEM-768 hybrid (default), X-Wing, and sealed boxes | MIT OR Apache-2.0 |
| [`aethel-core`](https://github.com/0x307/aethel-core) · [crates.io](https://crates.io/crates/aethel-core) | Production | Post-quantum anonymous identity: a separate identifier per context, no reusable public key, context-bound ML-DSA signing. Selective disclosure ships and is being hardened | Apache-2.0 |
| [`aethel-sdk`](https://github.com/0x307/aethel-sdk) · [crates.io](https://crates.io/crates/aethel-sdk) | Preview | The SDK over aethel-core: generate, sign, verify, project, recover. The place to start | Apache-2.0 |
| [`aethel-vault`](https://github.com/0x307/aethel-runtime) · [crates.io](https://crates.io/crates/aethel-vault) | Preview | Agent-held wallet: policy-gated x402 / EIP-3009 signing with ML-DSA-65 spend records | Apache-2.0 |
| [`pqc-privacy`](https://github.com/0x307/pqc-privacy) · [crates.io](https://crates.io/crates/pqc-privacy) | Lab | Research bundle, kept off every identity and payment path | MIT OR Apache-2.0 |

**Production** crates are thin, standards-bound libraries meant to be depended on today.
**Preview** crates work and are published, with APIs still settling. **Lab** crates are
research, never on an identity or payment path.

Also published: [`witan`](https://github.com/0x307/witan-gossip), a post-quantum gossip
protocol engine (ML-KEM-768 + ML-DSA-65) built as a WebAssembly component.

## Audit status

None of these crates has been independently audited, and none holds a CMVP / FIPS 140-3
validation. "FIPS 203/204/205/206" means the algorithms follow those standards, not that the
code is certified. Each repository's `SECURITY.md` lists its known issues and how to report a
vulnerability (security@0x307.com). Each `STABILITY.md` states what counts as a breaking
change and when a version is yanked.
