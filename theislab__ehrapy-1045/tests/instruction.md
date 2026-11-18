# Issue

**Title:** feat(preprocessing): add missing_data_mask function

## Description

## Summary

Add `ep.pp.missing_data_mask(edata)` to create boolean masks indicating missing values in EHR data matrices.

## Implementation

```python
ep.pp.missing_data_mask(
    edata,
    layer=None,           # Use edata.X or a specific layer
    mask_values=None,     # Additional sentinel values to treat as missing
    key_added="missing_data_mask",
    copy=False,
)
```

**Stores result in** `edata.layers[key_added]` as a dense boolean numpy array.

### Supported array types

| Type | Handler |
|------|---------|
| `np.ndarray` | `np.isnan()` + `np.isin()` |
| `sp.csr_array` / `sp.csc_array` | `.toarray()` → numpy path |
| `DaskArray` | `da.isnan().compute()` + `da.isin().compute()` |

### Files

| File | Change |
|------|--------|
| `ehrapy/preprocessing/_missing_data.py` | New: function + singledispatch handlers |
| `ehrapy/preprocessing/__init__.py` | Export (alphabetically after `_imputation`) |
| `tests/preprocessing/test_missing_data.py` | 10 tests covering all array types + edge cases |

### Pattern compliance

- `@use_ehrdata(deprecated_after="1.0.0")` decorator
- `singledispatch` for array type dispatch (dispatches on `mtx`, not `mask`)
- Keyword-only parameters after `edata`
- `copy` returns modified copy or `None`
- Google-style `Args:` docstrings

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9bf5ca1d8456`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.