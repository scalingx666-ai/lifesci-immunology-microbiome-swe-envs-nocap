# Issue

**Title:** Comparison of observed sequences to expected, the second

## Description

This is a follow-up PR to 

When expected abundances per sample are provided for matching sequences the following metrics will be generated for each sample in one file, and aggregated over all samples (mean, median, min, max) in another file:
- `observed`: Number of observed sequences
- `expected`: Number of expected sequences
- `TP`: Number of true positive sequences (observed and expected)
- `FN`: Number of false negative sequences (not observed but expected)
- `FP`: Number of false positive sequences (observed but not expected)
- `recall`: Recall of expected sequences = TP/(TP+FN)
- `precision`: Precision = TP/(TP+FP)
- `F1`: F1 score, the harmonic mean of the precision and recall = 2TP/(2TP+FP+FN)
- `Fbeta`: Fbeta score, the weighted F1 score. By default beta=2, i.e. weighs recall twice higher than precision
- `fdr`: False discovery rate = FP/(TP+FP)
- `jaccard`: Jaccard index = TP/(TP+FP+FN)
- `TPs_exp`: TP IDs (max 100) corresponding to expected sequences
- `FNs_exp`: FN IDs (max 100) corresponding to expected sequences
- `FPs_obs`: FP IDs (max 100) corresponding to observed sequences

A quick boxplot of some metrics is also generated, here an example (made-up data, not of a mock dataset):
<img width="500" height="400" alt="performance_boxplot" src="https://github.com/user-attachments/assets/87eac609-daef-48a7-b0a4-ca820025032d" />


#### Further PRs might add in tentative priority
(1) evaluate how abundances compare to expected
(2) compare taxonomic classification to expected

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e651b990cc8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.