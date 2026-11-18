# Issue

**Title:** Only save BAI index files when `--save_hostremoval_bam` specified

## Description

close #644 

Better handle generation and saving of BAM/BAI files.

- I've removed a redundant `SAMTOOLS_INDEX` process as the `minimap2` module already produces one.
- I've added better conditions for the BOWTIE2 associated SAMTOOLS_INDEX to only save BAI files when `--save_hostremoval_bam` is specified (like the BAM file), and defined the location to save alongside the BAM
- I've done the same for the `MINIMAP2` BAI file. 

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70560a8edf92`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.