# Contributing to 0x307

This is the standard for every public 0x307 repository. A repository's own
`CONTRIBUTING.md` may add rules for that repository; it never relaxes these.

We publish post-quantum cryptography that other people depend on. So the bar is about
evidence: every change shows that what it claims is true, and that it can't quietly break
something it doesn't mention.

## Who does what

| Role | Who | What they do |
|---|---|---|
| **Lead architect** | [@aytch4k](https://github.com/aytch4k) | Owns the cryptographic design. Approves every change to cryptographic code |
| **Maintainer** | [@eljay179](https://github.com/eljay179) | Reviews and merges pull requests, and cuts releases |
| **Contributor** | Everyone else | Opens pull requests. Never merges their own |

## Before you write code

- **Open an issue first** for anything beyond a small fix, and wait for a maintainer to
  agree to the change. It keeps you from spending time on something that can't be merged.
- **Security vulnerabilities:** don't open a public issue. Follow the repository's
  `SECURITY.md`.

## Pull requests

- **Every change arrives as a pull request from a branch.** Nobody pushes to `main`
  directly, and `main`'s history is never rewritten.
- **A maintainer who didn't write the change approves it.** Changes to cryptographic code
  also need the lead architect's approval.
- **Pull requests from 0x307 organization members are reviewed first.** Outside
  contributions are welcome and are reviewed after them, in the order they arrive.
- **One logical change per pull request.** Fill in the template: what changed, why, and
  how you verified it.
- **Link the issue** it resolves.
- **Say if you used AI assistance** substantially (writing code, tests or docs). That's
  fine, and it's held to exactly the same bar.

## The bar every change meets

**It builds and tests where it ships.**
- CI passes: build, tests, clippy and rustdoc with warnings denied, and lockfiles checked
  with `--locked`.
- The **packaged crate** (what crates.io serves) builds and passes its tests, not only the
  working tree.
- Every target the README claims (for example `wasm32-unknown-unknown`, `no_std`) builds.

**Its tests can fail.**
- New behaviour comes with a test that fails without the change.
- A test that something is **refused** also shows the valid case **accepted**. Otherwise
  it can't tell "refused correctly" from "refuses everything".
- Tests behind a feature use `required-features` in `Cargo.toml`. A file-level
  `#![cfg(feature = ...)]` compiles to an empty test binary that reports "0 passed" as
  success.

**What it claims is true.**
- README, docs and `CHANGELOG.md` are updated in the same pull request.
- A capability the docs describe has code and a test behind it.
- Breaking changes follow the repository's `STABILITY.md`: a version bump and a migration
  note.

## Cryptography

- **All post-quantum.** No classical asymmetric cryptography (RSA, elliptic curves,
  pairings) enters the dependency graph. The only exception is recorded and deliberate:
  `pqc-kem`'s X25519 + ML-KEM-768 hybrid, for key exchange. Maintainers check the resolved
  dependency graph of every change against a deny list of classical cryptography.
- **No new cryptographic constructions** without the lead architect's review. Composing
  existing, reviewed primitives is fine; inventing one is not.
- **Compare secrets and MACs in constant time**, never with `==`.
- **Randomness** comes from the operating system's CSPRNG, or entropy the caller
  supplies. Never a predictable source outside tests and benchmarks.
- **Nonces are generated inside the library.** They're never the caller's
  responsibility.
- **Signatures use a registered purpose** from `aethel-core`'s registry, never an ad hoc
  context string.
- **Secret material** is zeroized on drop, never logged, and never shown by `Debug`.
- **Failures don't reveal which check failed.**
- **Code never panics on untrusted input.** No `unwrap`, `expect` or unchecked indexing on
  data from outside.
- **No `unsafe`.** Our crates forbid it.

## Dependencies

- Explain every new dependency in the pull request: why it's needed, and why this crate.
- `cargo deny` stays clean: advisories, licences, bans and sources.
- Licences must be compatible with MIT OR Apache-2.0 (or Apache-2.0, for the crates
  licensed that way).

## What never goes into a public repository

- Links to private repositories, internal hosts, or internal trackers. Referring to an
  issue by its bare identifier is fine.
- Credentials, keys or tokens, even expired ones.
- Anyone's personal details without their permission.

## How pull requests are reviewed

Maintainers review contributions as an audit rather than a style check:
- The change is built from a fresh clone.
- The packaged crate is tested.
- Warnings are compared against `main`.
- The cryptography checklist above is applied.
- Every claim in the pull request is checked against evidence.

Findings come back specific and ranked. Anything that breaks a security property, or a
claim that isn't backed by code, has to be fixed before merge.

## Releases

Maintainers publish releases, from a clean clone of `main` whose contents match what CI
tested, and tag them.

## Code of conduct

These projects follow the [Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/),
unmodified.
