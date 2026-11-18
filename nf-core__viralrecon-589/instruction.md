# Issue

**Title:** Fix trivial Nextflow strict syntax lint errors, add full implementation plan

## Description

## Summary                                                                                                                                           
  Nextflow strict syntax compliance is becoming mandatory for nf-core pipelines. This PR begins addressing the 49 lint errors in viralrecon, following 
  a phased implementation plan added to `docs/strict_syntax_fix_plan.md`. This PR covers Phase 1 (trivial fixes):

  - Remove nonexistent `test_full_sispa` profile entry from `nextflow.config`
  - Rename shadowed variables in `modules/local/sierralocal/main.nf` (script-block vars now suffixed with `_arg`)
  - Rename shadowed closure params in `subworkflows/local/consensus_bcftools/main.nf`
  - Replace `Nextflow.error()` with `error()` in `main.nf`

  Resolves 13 of 49 `nextflow lint` errors.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6ed385bbdfbe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.