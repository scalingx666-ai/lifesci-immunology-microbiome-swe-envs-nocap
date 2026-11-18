# Issue

**Title:** Fix conda CI errors

## Description

This should fix the failing CI conda checks like [this one](https://github.com/nf-core/funcscan/actions/runs/17852193803/job/50804797018?pr=497#step:4:1019), as discussed on Slack [here](https://nfcore.slack.com/archives/C04QR0T3G3H/p1758186889529689?thread_ts=1758020637.890609&cid=C04QR0T3G3H).

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4ba2988dcca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.