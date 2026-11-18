# Issue

**Title:** Pin pynndescent<0.7 and fix docs warnings

## Description

CI on `main` is currently broken by upstream releases. #1208 shows the same failures.

### pynndescent 0.7.0 (released 2026-10-27) breaks scanpy 1.12.4
- `sc.pp.neighbors` fails with `'csr_array' object has no attribute 'getnnz'` (scverse/scanpy#4444), which breaks the `subgroups` notebook.
- `sc.tl.ingest` passes `NNDescent.n_search_trees`, now deprecated and `None`, to `make_forest`. This breaks `test_ingest*` and the `ingest` docstring example (`TypeError: unsupported operand type(s) for *: 'NoneType' and 'int'`).

Temporarily pin `pynndescent<0.7` until scanpy supports it.

### Docs warnings (nitpicky, `-W`)
- `famd` was the only public `singledispatch` function. Recent autodoc renders the registered implementations as extra signatures with unresolved string annotations (`EHRData`, `np.ndarray`). It now dispatches in a private `_famd`, like the other `singledispatch` functions in ehrapy. No behavior change.
- Sphinx 9.2 resolves type aliases as `py:type`, so `Statistic` is now also ignored under that role.

### Checks
- `sphinx-build -W` passes locally (Python 3.14, Sphinx 9.2.0, sphinx-autodoc-typehints 3.17.4). Before this change, the same build failed with these 5 warnings.
- All `ingest`/`famd` tests and docstring examples pass locally (Python 3.12, pynndescent 0.6.0).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2f664edeb1e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.