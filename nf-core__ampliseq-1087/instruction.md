# Issue

**Title:** Replace workflow overview figure with simplified metro map

## Description

Replace workflow overview figure with simplified metro map & add the metro map as `manifest.diagram`.

Simplifications include:
- ONT & Illumina both default
- crossover ONT to Illumina (theoretically, someone could set for Illumina data Savont, or for ONT data DADA2, but would need explicit overwriting)
- DADA2 steps heavily simplified
- every single step is optional. One of DADA2 and Savont must run when raw reads are input. With ASV intermediate input, even those are omitted. However, ASV input isnt shown because most downstream stuff isnt compatible then (no abundance profile!). So I opted not to loop around optional steps.
- The "Limited" is also a simplification: only some taxonomic references (3) can have an "extraction" with primers, and only DADA2 (but more to come) taxonomic classifications (4) can be "consolidated". Additionally, each taxonomic classifier (4) has only a subset of taxonomic references (3) but with more or less large overlaps. It would add a lot of noise to the figure to add that info. Thats in the usage docs though.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/ampliseq _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b60e549d96d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.