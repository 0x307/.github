## What changed

<!-- One logical change. What does this pull request do? -->

## Why

<!-- The problem it solves. Link the issue: Closes #... -->

## How I verified it

<!-- Commands you ran and what they showed. Evidence, not assertions. -->

## Checklist

- [ ] CI passes (build, tests, clippy and rustdoc with warnings denied, `--locked`)
- [ ] The packaged crate builds and tests (`cargo package`, then test the unpacked crate)
- [ ] New behaviour has a test that fails without this change
- [ ] Tests that something is refused also show the valid case accepted
- [ ] README, docs and `CHANGELOG.md` updated, and every claim matches the code
- [ ] No new cryptographic construction (or: the lead architect has reviewed it)
- [ ] New dependencies explained below; `cargo deny` clean
- [ ] Nothing private: no internal links, hosts, credentials or personal details
- [ ] Breaking changes follow `STABILITY.md` (version bump, migration note)

## Dependencies added

<!-- Each new crate and why. "None" if none. -->

## AI assistance

<!-- None, or what was AI-assisted (code, tests, docs) and how you checked it. -->
