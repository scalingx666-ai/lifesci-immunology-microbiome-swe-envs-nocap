# Issue

**Title:** Add lazy DATA helpers (only_text docs, as_memmap, read_events)

## Description

## Summary
- Document and stabilize `only_text=True` as the supported metadata probe (README + `FlowData` docstring); retain DATA offsets / dtype metadata for later lazy access.
- Add `data_byte_range`, `numpy_dtype()`, `as_memmap()`, and `read_events(indices=...)` for uniform `$DATATYPE=F`/`D` layouts; raise `UnsupportedLazyDataError` for ASCII, integer, variable bit-width, and in-memory handles without a path.
- **`read_events(..., preprocess=True)`** — default matches `as_array()` (gain/log/timestep). Shared `_apply_preprocessing()` keeps lazy and eager paths aligned. Use `preprocess=False` or `as_memmap()` for raw stored DATA.
- `ignore_offset_error` warning parity on the lazy mmap offset correction path.
- Unit tests on existing `data/fcs_files/` fixtures (little- and big-endian float, integer rejection, variable-bit rejection, preprocess default vs `as_array()`).

### Three-tier lazy access model
| API | Output |
|---|---|
| `as_memmap()` | Raw on-disk values, mmap, native dtype |
| `read_events(..., preprocess=False)` | Raw stored DATA, float64, copied/subset |
| `read_events()` / `as_array()` | Preprocessed float64 (default) |

Closes / related:

## Test plan
- [x] `PYTHONPATH=src python3 -m pytest tests/test_lazy_data.py tests/test_flowdata.py -q` (30 passed)
- [x] `read_events()` default preprocess matches `as_array(preprocess=True)` on lazy path
- [ ] Review docstring / README wording for `only_text` + lazy helpers
- [ ] Confirm memmap path does not change existing full-load behaviour

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3880a63766e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.