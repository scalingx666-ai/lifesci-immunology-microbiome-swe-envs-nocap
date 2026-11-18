# Issue

**Title:** Change default for --dada_ref_taxonomy

## Description

Change default for `--dada_ref_taxonomy` from `silva=138.2` to `sbdi-gtdb=R11-RS232-1`, because the former is outdated. The latter, based on GTDB, lacks eukaryotes however. So SILVA might have still its uses.

Updated the overview figure accordingly. Also added missing entries for most recent sbdi-gtdb & gtdb entries into the schema.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `949884e25f4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.