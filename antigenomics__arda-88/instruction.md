# Issue

**Title:** arda 2.6.3 — `pip install 'arda-mapper[mmseqs]'` no longer fails

## Description

The `mmseqs` extra depended on `arda-mmseqs`, which CI builds but which has never been uploaded
to PyPI. An extra naming a package the index does not have is a resolution **error**, not a
soft skip — and that exact command was what the README, the docs and `mmseqs_binary()`'s own
"binary not found" message all recommended.

Now an empty alias like `rnaseq`, so existing pins keep resolving. The bundled wheel was only
ever a convenience over the runtime auto-fetch, which pulls the same static binary and needs the
network exactly once — as pip itself just did.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `765d35a2cc33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.