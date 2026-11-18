# Issue

**Title:** Drop leidenalg flavor from ep.tl.leiden (igraph only)

## Description

## Summary

- Removes `flavor`, `partition_type`, and `directed` parameters from `ep.tl.leiden`; always forwards `flavor="igraph"` to `scanpy.tl.leiden`.
- Drops the `leidenalg.VertexPartition.MutableVertexPartition` `TYPE_CHECKING` import in `ehrapy/tools/_scanpy_tl_api.py`.
- Cleans up `docs/conf.py`: removes `"leidenalg"` from `autodoc_mock_imports` and removes the four leidenalg-related entries in `nitpick_ignore`.
- `igraph` is already a hard dep, so no `pip install ehrapy[leiden]` extra or runtime install hint is needed.
- Non-breaking for in-tree callers: tests, plot docstrings, and tutorial notebooks only pass `resolution` / `key_added`.

Fixes

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac70d479f6e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.