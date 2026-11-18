# Issue

**Title:** Cache CI datasets and harden against flaky downloads

## Description

**Problem**
CI jobs download example datasets (mimic_2, diabetes_130_fairlearn, …) from upstream hosts such as physionet.org on every run. When those hosts are slow, rate-limiting, or down, the test and notebook jobs fail or hang — a recurring source of red CI that has nothing to do with the change under test. This mirrors the issue fixed in ehrdata (); this PR ports the same approach to ehrapy.

**Changes**
Dataset downloads in ehrapy are fully delegated to the ehrdata submodule (the legacy in-repo `ehrapy/data/_dataloader.py` was removed in #1016), so no Python changes are needed here — ehrdata's downloader already short-circuits when a file exists and already has the resilient retry loop. This PR is CI-only.

`.github/workflows/test_cpu.yml` (test job):

Restore `ehrapy_data/` before the run via `actions/cache/restore@v4`, key ehrapy-data-tests-v1 (static, shared across the Python matrix).
Save the cache only on `cache-hit != 'true' && success()`, so a partial/failed download is never persisted under the immutable key.
Set `EHRDATA_DOWNLOAD_MAX_RETRIES=5 / EHRDATA_DOWNLOAD_RETRY_DELAY=10` on the test step so a genuinely unreachable host fails fast instead of hanging.
.github/workflows/run_notebooks.yml (notebook job):

Same restore/save pattern, but keyed per notebook (`ehrapy-data-notebook-${{ matrix.notebook }}-v1`) since each tutorial pulls a different subset.
Cache path is `docs/tutorials/notebooks/ehrapy_data` — nbconvert executes with the notebook's directory as the working directory, and ehrdata's DEFAULT_DATA_PATH is the relative ehrapy_data, so downloads land there.
Same EHRDATA_DOWNLOAD_* env vars on the execution step.

**How caching works here**
ehrdata's `_download()` returns early when the target file already exists, issuing no network request. So once a cache is populated, a cache hit means the datasets are present on disk and the loaders never touch the network. The first run after a key bump is a cache miss that downloads and then saves; every subsequent run restores.

**Why the immutable-key guard matters**
actions/cache keys are write-once. Saving only after a green run that actually downloaded prevents a truncated download (e.g. a request that died mid-stream) from being sealed into ehrapy-data-*-v1 and breaking every future run. Bump the -v1 suffix when a dataset URL changes.

**Verification**
Ran the two networked loaders locally through the same ehrdata submodule code and default path CI uses:

ed.dt.mimic_2() → downloaded, shape (1776, 46, 1)
ed.dt.diabetes_130_fairlearn() → downloaded, shape (101766, 22, 1)
Confirmed: (1) cold download fetches and parses both; (2) a warm re-run does zero network calls and returns instantly — the exact behavior a cache hit relies on; (3) the active ehrdata submodule has the fixed retry guard (retry_count < max_retries).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d368ac77b58e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.