# Issue

**Title:** Fix --skip_binqc failing on undefined bin QC and GTDB-Tk outputs

## Description

Running with `--skip_binqc` (and all bin QC tools disabled) failed on `dev`:

1. `No such variable: ch_busco_summary`: the BUSCO, CheckM and CheckM2 summary channels were only defined inside the `if (!params.skip_binqc)` block, but `BIN_SUMMARY` always reads them.
2. `Access to 'GTDBTK.out' is undefined`: the GTDB-Tk MultiQC files were collected whenever `--skip_gtdbtk` was unset, but GTDB-Tk also requires bin QC to run.

## Changes

- The three summary channels are initialised as empty, like `ch_bin_qc_metrics`.
- GTDB-Tk MultiQC files are collected right after `GTDBTK` is invoked.

## Testing

- `-profile test --skip_binqc --run_busco false` completes, producing `bin_summary.tsv` and the MultiQC report.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`). The only failure is `files_unchanged` for `assets/nf-core-mag_logo_light.png`, also present on `dev`.
- [x] Ensure the test suite passes.
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fbb2153e338`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.