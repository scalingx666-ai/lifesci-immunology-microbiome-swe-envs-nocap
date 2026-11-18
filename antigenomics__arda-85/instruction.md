# Issue

**Title:** ci: unblock the 2.6.0 PyPI publish (Windows pip) and the arda-mmseqs upload

## Description

Two CI-only fixes, no source change.

`pip install --upgrade pip` in the wheel smoke test resolves to `pip.exe` on Windows, which
refuses to replace its own running executable. All four Windows legs failed on the v2.6.0 release
and `publish` needs `test-wheels`, so a fully green build produced no PyPI upload.

The `arda-mmseqs` version guard compared `mmseqs version` — which prints the build's git commit,
`8cc5ce367b...` — against the release tag `18-8cc5c`, and so rejected a correct build. It now
checks the upstream release tag directly, which is what `releases/latest/download` resolves
against anyway.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `825d9e77a6c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.