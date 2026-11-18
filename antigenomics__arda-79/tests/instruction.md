# Issue

**Title:** Release 2.5.7 — use the committed mmseqs indexes + version bump

## Description

Cuts **2.5.7**. Headline fix + the version bump; the reference is unchanged.

## Fix — the committed precompiled indexes were never used

The precompiled mmseqs DBs shipped in `database/vdj/*/mmseqs/` are gated on a version marker compared with an exact `==`. But `mmseqs version` prints the same release+commit with different punctuation across builds — the official static binary says `18-8cc5c`, the bioconda build `18.8cc5c`. When arda's toolchain moved from conda's mmseqs to the static binary (#78), every committed marker (written under conda's mmseqs) stopped matching, so the shipped indexes were silently ignored and every run rebuilt a private `data/mmseqs_db` cache.

`_committed_index` and `build_index` now compare via `mmseqs.version_key` — folds `[\s._-]+`→`-` and lowercases — bridging the cosmetic difference while still rejecting a genuinely different version (`17-b804f` ≠ `18-8cc5c`). Verified: the committed nt/aa indexes for every org are now selected, and the full unit + synthetic + realworld suite is green **using them** (303 passed).

## Version bump 2.5.6 → 2.5.7

All eight places: `pyproject.toml`, `src/arda/__init__.py`, `docs/conf.py`, `docs/pipeline_integration.rst`, and the Nextflow module's `main.nf` / `environment.yml` / `Dockerfile` / `README.md`. The `pypi` publish job validates pyproject == tag.

## CHANGELOG

`## 2.5.7` covers this fix plus the two already-merged into master since 2.5.6: the stale-cache rebuild (#77) and the conda→uv toolchain switch (#78).

## Release checklist
- [x] `scripts/pack_reference.sh` pre-flighted locally (2.8M, 53 members, verified — the `reference-asset` job will attach `arda-reference-vdj.tar.gz`)
- [ ] Merge → cut GitHub Release `v2.5.7` → `publish.yml` builds wheels/sdist and pauses at the **`pypi`** environment gate for approval

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec692933e100`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.