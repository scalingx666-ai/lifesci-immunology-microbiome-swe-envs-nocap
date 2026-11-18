# Issue

**Title:** arda 2.6.2 — auto-fetch no longer stages downloads in /tmp

## Description

Both auto-fetches unpacked into `tempfile.TemporaryDirectory()`. On a cluster `/tmp` is routinely
a small node-local disk — aldan3's is **2.0 GB with 29 MB free** — and the IgBLAST fetch, a
~400 MB archive that extracts to more, died there on its first real run with
`OSError: [Errno 28] No space left on device`.

Staging under `dest.parent` fixes it, and makes download → extract → lay out → `os.replace`
single-filesystem by construction rather than by assumption. mmseqs had the identical bug.

Invisible on any machine with a roomy `/tmp`, so the test asserts where the archive is written.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5cff5227ceb3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.