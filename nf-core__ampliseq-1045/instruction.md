# Issue

**Title:** Fix DADA2_ADDSPECIES crash on ITS-trimmed sequence collisions

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Description

.

`addSpecies()` requires its taxtable's row names to be unique ACGT sequences. When `--cut_its` causes two ASVs to become identical once trimmed to just the ITS region (they differ only in flanking rDNA, which gets discarded), R silently disambiguates the duplicate row name by appending `.N` — and that literal `.N` then fails `addSpecies()`'s ACGT check, crashing the whole run with a misleading "Non-ACGT characters present in the query sequences" error.

Fix: classify each unique sequence once, then map the resulting `Species` call back onto every original row — keeping each row's own `ASV_ID` and confidence values intact (rows sharing a sequence get the same `Species` result, but nothing else is merged between them; an earlier version of this fix got that wrong and accidentally merged `ASV_ID`s too, caught by a downstream `TREESUMMARIZEDEXPERIMENT` failure on duplicate row names).

`conf/test_pacbio_its.config` previously worked around this by setting `skip_dada_addspecies = true` — that workaround is removed, so this profile is now real regression coverage for the bug. Verified the common, non-colliding case is unaffected by re-running `tests/default.nf.test` *without* `--update-snapshot` (zero diff against the existing snapshot).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9d44ae8a460`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.