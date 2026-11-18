# Issue

**Title:** Add abundance metrics

## Description

This is a follow-up PR to 

With this PR the comparison of observed to expected _sequences_ is finished for now, I think. The results are not (yet) integrated to the pipeline summary report though.
A comparison of observed to expected _taxa_ would be also great in future. Changing the test datasets to _mock_ data could make the comparison also in tests meaningful.

This PR adds metrics based on abundances:

- `pearson_cor`: Pearson's Correlation (cor)
- `spearman_rho`: Spearman's Rank Correlation (rho)
- `deviation`: Median Percent Abundance Deviation
- `mae`: Mean Absolute Error (MAE)
- `rmse`: Root Mean Square Error (RMSE)
- `ps`: Proportional Similarity (PS)
- `bray-curtis`: Bray-Curtis Dissimilarity
- `hellinger`: Hellinger Distance
- `jensen-shannon`: Jensen-Shannon Divergence

and figures thereof, e.g. 
<img width="933" height="693" alt="image" src="https://github.com/user-attachments/assets/13e901fc-a8a5-40f7-ba62-836bdfec737c" />

and fixes a shortcoming in the previous PR that limited the blast result filtering.

Additionally, `--expected_sequences_mismatches` was added. It allows to increase the threshold for mismatches/gaps to call a TP. For example, `--expected_sequences_mismatches 1` also allows observed sequences with 1 mismatch to an expected sequence to be accepted as TP (by default only exact matches, i.e. `--expected_sequences_mismatches 0`).

Previously, the comparison results were published in a folder that included the params md5sum in its path. While this was great for repeatedly resuming the pipeline with various parameters and accumulating all results in a single outdir directory, it proofed difficult: the CI tests seemed to not like missing files (md5sum changed when param was added) and md5sums were different between local & CI nf-test run due to differing parameter string. Therefore, the comparison results are now not published under a md5sum, but overwritten each time. The md5sum_version.txt still has all that info though.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [x] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd3b56556d2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.