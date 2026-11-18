# Issue

**Title:** fix DADA2 tracking table

## Description

Closes 

AI writes:
            # Align columns by merging on the normalised sample key instead of cbind'ing
            # independently (re)sorted columns. The old positional cbind shifted rows when a
            # sample name was a full prefix of another sample name (e.g. EQUIP_BLANK / EQUIP_BLANK_3_25_2026),
            # mis-labelling the denoised/merged/nonchim read counts in the HTML report.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `827a6b77be8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.