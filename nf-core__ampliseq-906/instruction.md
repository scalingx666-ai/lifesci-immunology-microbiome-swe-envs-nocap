# Issue

**Title:** fix consensus merge pairs with one sample run

## Description

When a run contains only one sample and the option `mergepairs_strategy: "consensus"` is used, the workflow fails at `NFCORE_AMPLISEQ:AMPLISEQ:DADA2_STATS`. 

IN `NFCORE_AMPLISEQ:AMPLISEQ:DADA2_DENOISING` with `mergepairs_strategy: "consensus"` the R object `mergers` is converted from a data.frame into a list when only one sample is analysed for the consensus section of the code to work with single sample and multiple samples runs. However, in case of a single sample run `DADA2_STATS` is expecting a data.frame and not a list.

To fix that bug, I have added in `dada2_denoising.nf` a piece of code converting back `mergers` to a data.frame in case of a single sample run.

## PR checklist

- [X] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [X] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [X] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c81f874abb5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.