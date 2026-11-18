# Issue

**Title:** Fix test suite for ehrdata_blobs()'s old 2D-.X default

## Description

**Changes**

- `submodules/ehrdata`: bumped to include theislab/ehrdata#285.
- `tests/conftest.py`:
    - edata_blob_small: now explicitly requests the tensor via `layer=DEFAULT_TEM_LAYER_NAME` and derives a 2D .X snapshot from it, so the 15 tests that usethis fixture as 2D data (PCA, neighbors, encoding, outliers, survival analysis, etc.) keep working, while tests/plot/test_timeseries.py's use of the same fixture's 3D `layers[DEFAULT_TEM_LAYER_NAME] `still works too.
     - edata_blobs_timeseries_small: layer_2 now copies from `layers[DEFAULT_TEM_LAYER_NAME]` instead of the now-None .X.
- `tests/plot/test_sankey.py`: pass` layer=DEFAULT_TEM_LAYER_NAME` explicitly to `ehrdata_blobs()` in the three tests that need the named layer to exist.
- `tests/tools/test_embeddings.py`: `test_famd_ehrdata_integration` derived its single-timepoint layer from` edata.X` (now None); reworked to slice it from the existing 3D layer instead.
     
- `tests/preprocessing/test_quality_control.py`:
    - _make_mar_edata: squeezes the 3D-time .X before doing 2D-style indexing
   - Regenerated the hardcoded pyampute reference values (`tests/data/preprocessing/mcar_refs`) that this helper feeds, fixing the squeeze changes the actual data generated (the old 2D-snapshot logic had a bug where missingness wasn't always propagated correctly), so the old reference numbers no longer apply.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44dad26d7873`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.