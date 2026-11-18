# Issue

**Title:** feat: Add bakta to run modules in multiqc

## Description

* Added `bakta` to the `run_modules` list in `multiqc_config.yml`, enabling Bakta output in MultiQC reports ().
* Added a `Bakta` section to `table_columns_visible` to control column visibility for Bakta results.
* Added `bakta_fn_snames: true` to enable sample name formatting for Bakta results.

Tested by checking the output of  ` nf-test test tests/test_bakta.nf.test --profile test_bakta,docker`

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/funcscan/tree/main/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/funcscan _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `195ec2a389fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.