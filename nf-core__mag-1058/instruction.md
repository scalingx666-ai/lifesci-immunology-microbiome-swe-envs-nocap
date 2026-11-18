# Issue

**Title:** fix: gzipped files on METABINNER_BINS to prevent race condition

## Description

When running MetaBinner on our HPC (storage mounted via NFS), I got the following error:
```
find: ./bins/.nfs000000100122bb1600001c93: No such file or directory
```
This happens because when find starts, the file is still visible in the NFS filesystem, but by the time the `mv` command runs, the file has already been unlinked, throwing an error.
This chamge makes the script generating the bin files gzipped, so the post-execution of gzip and mv is no longer required.

This also changes the boundary of too short bins (`<` to `<=`) to align with what the tool does.

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/mag/tree/main/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/mag _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46419491d41e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.