# Issue

**Title:** RGI add parameter to save json files

## Description

In this PR:
- CHANGE: RGI outputs by default only `.txt` and have added the `arg_rgi_savejson` parameter to give the user the option to save it as part of the RGI output dir if required.
- REASON: We noticed that RGI outputs HUGE `.json` files, which are quite bulky and are not required downstream in the pipeline. 
-  CLOSES issue #245 

**TODO**
- [x] Usage Documentation in `docs/usage.md` is updated. NOTYET!!!
- [x] Output Documentation in `docs/output.md` is updated. NOTYET!!
- [x] `CHANGELOG.md` is updated. NOTYET!!
- [x] `README.md` is updated (including new tool citations and authors/contributors).
 
## PR checklist

- [x] This comment contains a description of changes (with reason).
- [] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/master/.github/CONTRIBUTING.md)- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66b9a11c5c46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.