# Issue

**Title:** Use small CheckM2 database in test_alternatives

## Description

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nf-test test tests/test_alternatives.nf.test --profile=+singularity`).
- [x] `CHANGELOG.md` is updated.

## Description

- Updates `checkm2/predict` to include nf-core/modules#13019: the database is now passed via the `CHECKM2DB` env var instead of `--database_path`, which skips CheckM2's hardcoded database checksum check and allows reduced databases.
- `test_alternatives` now uses the small CheckM2 DIAMOND database already available in test-datasets (`modules/data/delete_me/binette_checkm2/binette_checkm2_small_db.dmnd`) instead of downloading the full CheckM2 database (so `CHECKM2_DATABASEDOWNLOAD` no longer runs there).
- Snapshot updated accordingly: CheckM2-derived outputs change (report, bin summary, MultiQC CheckM2/general stats), one fewer task, and fewer DIAMOND hits (803 → 33, still non-empty). Verified stable across two runs.

`test_full` is unchanged and still uses the full database.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0cb2b53d83e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.