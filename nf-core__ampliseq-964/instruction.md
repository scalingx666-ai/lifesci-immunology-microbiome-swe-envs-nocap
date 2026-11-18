# Issue

**Title:** Enable local reference storage directory

## Description

Closes 

When using the newly added parameter `--ref_taxonomy_storage`, remote taxonomic reference databases will be re-used from a local reference storage directory. That avoids downloading remote reference databases multiple times when working on the same compute resource but in a different working directory.

The changes appear here larger than they are, because database retrieval was a bit scattered in the ampliseq.nf script and I wanted to standardize it. I also considered (and tested) to use a subworkflow, but that complicated the matter because values (val_*) were emitted instead as channels.

To not accidentely use a wrong file when using the reference storage directory, each reference database file must have a unique file name in `conf/ref_databases.config`, and I added a verification step into `subworkflows/local/utils_nfcore_ampliseq_pipeline/main.nf`.

Potential issues:
- The added module is local, the nf-core wget module could be used, but would require modifications and/or extensive config & channel operations

I verified strict syntax compliance with
```
NXF_VER=25.10.2 nextflow lint ampliseq -exclude ".git,.nf-test,nf-test.config"
NXF_VER=26.02.0-edge nextflow lint ampliseq -exclude ".git,.nf-test,nf-test.config"
NXF_VER=26.02.0-edge NXF_SYNTAX_PARSER=v2 nextflow run ampliseq --help
```

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bade6c43081c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.