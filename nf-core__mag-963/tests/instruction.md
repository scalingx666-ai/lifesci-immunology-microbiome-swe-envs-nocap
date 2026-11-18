# Issue

**Title:** Summarise ancient DNA pyDamage results per bin and add to bin summary table

## Description

To close #833 

Supersedes  Nextflow only version in #835 (which was having problems with data-flow consistency) with a python script only method.

Essentially:

1. Makes a contig to bin map
2. Separates per-contig pydamage results
3. Groups per-contig pydamage result per bin assignment (save)
4. Summarises pydamage contig results per bin with a median value
5. Attaches the median summaries to the bin_summary.tsv    

Additional minor changes:

- Fixes the official pyDamage results unnecessarily publishing `versions.yml` alongside the actual results
- Minor reformatting in `mag.nf` based on language server 

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a8102e5d301`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.