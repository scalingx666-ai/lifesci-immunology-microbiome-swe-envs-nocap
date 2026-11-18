# Issue

**Title:** Release v2.5.1 — bump engines to latest (seqtree 0.4.0, vdjmatch 0.1.0, arda 2.5.5)

## Description

## v2.5.1 — engine floors bumped to latest

All three antigenomics engines to their newest PyPI releases:

| Engine | Was | Now |
|---|---|---|
| arda-mapper | >=2.5.5 | **>=2.5.5** (already latest) |
| seqtree | >=0.3 | **>=0.4.0** |
| vdjmatch | >=0.0.1 | **>=0.1.0** |

`vdjmatch 0.1.0` itself requires `seqtree>=0.4.0`, so the floors are mutually consistent; seqtree 0.4.0 still has **zero** base runtime deps.

**No vdjtools code change was needed** — despite the seqtree 0.3→0.4 and vdjmatch 0.0.1→0.1.0 jumps, no API broke.

### Verification
- 396 fast tests
- Full slow tier (17) — incl. the stitch → arda-annotate round-trip and exhaustive Pgen
- C++ `ctest`
- CI green on all 6 jobs (Python 3.10/3.12 × Linux/macOS)

Base deps remain: `arda-mapper>=2.5.5`, `seqtree>=0.4.0`, `vdjmatch>=0.1.0`, `huggingface_hub`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f724b43c3bb8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.