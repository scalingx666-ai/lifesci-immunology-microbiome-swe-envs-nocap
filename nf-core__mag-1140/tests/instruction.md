# Issue

**Title:** Fix overflow in Tiara bin domain classification softmax (large eukaryotic bins labelled prokarya)

## Description

`bin/domain_classification.R` applied a softmax to summed per-contig Tiara probabilities using plain `exp()`. For bins with many contigs the sums exceed ~709, `exp()` overflows to `Inf`, and the probabilities become `NaN`; `which.max()` then skips the `NaN` and falls back to the first class (`prokarya`). This PR uses the standard log-sum-exp form (subtract the row maximum before `exp()`), which is mathematically identical but cannot overflow.

- Results are unchanged for bins that previously did not overflow.
- Large eukaryotic bins are now correctly classified as `eukarya`.

Tested on a 2-sample pilot (MEGAHIT + metaSPAdes; MetaBAT2, CONCOCT, SemiBin2): re-running the patched script on the 12 pilot `TIARA_CLASSIFY` inputs, all 15 bins previously at `0 NA 0 0` changed from `prokarya` to `eukarya` (4.4–42.5 Mb; all Chlorophyta by CAT, 4–51% complete by BUSCO `chlorophyta_odb10`), and the other 94 bins kept their classification. This included two *Nitrosomonas* bins confirmed by GTDB-Tk, which correctly stayed `prokarya`.

## Acknowledgement

This bug was identified and the fix developed with the assistance of Claude Opus 5.5 (Anthropic), an AI model. I reviewed the change and tested it on our pilot data (see above).

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f339384b051`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.