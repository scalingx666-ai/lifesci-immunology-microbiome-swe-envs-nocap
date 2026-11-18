# Issue

**Title:** Add comparison to taxonomic profile

## Description

This addition allows to supply an expected taxonomic profile that is compared to the observed taxonomic profile that is produced by the pipeline. It iterates through all common taxonomic levels and calculates a plethora of performance parameters. New parameter `--expected_profile` to supply the expected taxonomic profile.

`test_savont` was extended with a test file that was deposited at test-datasets, see 

Of that test, the visualisation `profile_lineplot.png` is:
<img width="600" height="400" alt="profile_lineplot" src="https://github.com/user-attachments/assets/3dbd0d8d-b4de-4fdf-a1aa-de2fcfc10039" />

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [x] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e5dc4925c5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.