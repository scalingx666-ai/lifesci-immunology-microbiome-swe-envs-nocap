# Issue

**Title:** Fix test_single_end snapshot flakiness from CPU-dependent floating-point outputs

## Description

<!--
# nf-core/mag pull request

Many thanks for contributing to nf-core/mag!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/mag/tree/main/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test_single_end,docker --outdir <OUTDIR>`).
- [x] `CHANGELOG.md` is updated.

## Description

Split out of #1110, where I ran into this as an unrelated, pre-existing flakiness issue while working on study-wide bin dereplication.

`test_single_end` CI runs were intermittently failing on `nf-test`'s exact-hash snapshot comparison for several files: `MEGAHIT-{CONCOCT,MaxBin2}-*_pydamage_bin_results.tsv`, `pydamage_bins_summary.tsv`, `bin_summary.tsv`, and (unexpectedly) geNomad's `*_virus_summary.tsv`.

**This went through two iterations while I chased it down (visible in the commit history):**

1. First I assumed it was thread-count-dependent floating-point non-associativity in `CONCOCT_CONCOCT`/`MAXBIN2` (both pass `$task.cpus` as their thread count, and `test_single_end`'s `resourceLimits` gives them more than one CPU) -- the same class of issue `GTDBTK_CLASSIFYWF` already works around in this profile. I pinned both to `cpus = 1` and verified the fix worked identically across two different physical machines.
2. But CI kept failing anyway, on the exact same files, even with the pin in place. Investigating further: CI runs on a `runs-on`-provisioned AWS instance (`m8i-flex.xlarge`), a different CPU generation than either machine I'd verified against. And critically, geNomad's `*_virus_summary.tsv` -- which has nothing to do with binning or thread count at all -- showed the identical pattern: stable across my two machines, consistently different on CI.

That ruled out thread count as the cause. What all the affected files actually have in common is that they're floating-point-derived numeric outputs (ancient-damage statistics, viral classification scores) sensitive to the CI runner's specific CPU (likely something like BLAS/numpy's runtime SIMD dispatch choosing a different code path per CPU generation, though I haven't pinned that down further). The actual bin *composition* -- `.fa.gz` bin files, CONCOCT's `clustering_gt1000.csv` -- never differed across any environment in any of my captures, pinned or not.

So this PR now takes a different approach: **exclude those specific floating-point-derived files from the exact-hash snapshot comparison via `.nftignore`, and replace them with content assertions** (row counts, parseability, and for `pydamage_bins_summary.tsv`, an exact row-count match against the number of per-bin result files it should summarize -- see `bin/summarise_pydamagebins.py`), matching the pattern the test file already used for `bin_summary.tsv`. The `cpus = 1` pin turned out to be unnecessary once these files stopped being hash-compared, and re-verifying across the same two machines with it reverted confirms bin composition itself is unaffected either way -- so it's not included here.

### Worth discussing

I don't have a firm read on whether "exclude + content-check" is the right general pattern for outputs like this, or whether it's worth chasing the actual CPU-dispatch root cause further (e.g. pinning a specific BLAS backend). Opening this as a small PR specifically to get your take, since the same underlying issue likely affects other floating-point-heavy tools in this pipeline's test suite (CheckM2's neural net scoring is one candidate) and may come up again.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01NJ75Ui2JZjJwJ7T7o5acvg

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6b6452f4337`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.