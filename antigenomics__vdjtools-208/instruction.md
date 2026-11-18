# Issue

**Title:** Fix single-cell CI dependency and Dandelion backend compatibility

## Description

Fix the failing single-cell CI jobs: constrain Zarr to <3 on Python 3.10, where AnnData rejects Zarr 3; explicitly construct Dandelion 1.0's pandas class so the existing bridge and metadata updates keep working without PyArrow or changing the caller's backend.

Validation: 41 affected tests pass with Dandelion 1.0 and no PyArrow (16.89 s), focused Ruff checks pass, and AnnData 0.11.4/Zarr 2.18.3 import in a fresh Python 3.10 environment. Editable package build passes.

Scope verified against GitHub compare/master...dev and local origin/master...dev: exactly one commit, 437db6a, changing only pyproject.toml, python/vdjtools/sc/dandelion.py, and tests/python/test_sc_interop.py (17 insertions, 4 deletions). No native kernels or binary fixtures differ from master. No version bump or release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4652d6c6b59d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.