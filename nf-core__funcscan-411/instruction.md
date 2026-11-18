# Issue

**Title:** Fix hamronization fargene input

## Description

This optimizes which hits from fARGene are summarized by hAMRonization: Before this PR, 2 files were in the hmmsearch output channel, but only one is required (the one starting with `retrieved-genes-`, as can be seen in the fARGene [documentation](https://github.com/pha4ge/hAMRonization?tab=readme-ov-file#usage):

![image](https://github.com/user-attachments/assets/3913d3a3-6ba8-4168-94c2-4d2649e70eee)

Now, after the fargene module update, the ARG subworkflow pics the correct fargene output channel as input for hAMRonization and only the corrects show up in the final summary file (`results/reports/hamronization_summarize/hamronization_combined_report.tsv` tested and verified locally).

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [x] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `04195adca3f2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.