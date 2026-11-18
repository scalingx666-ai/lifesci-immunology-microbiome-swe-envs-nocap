# Issue

**Title:** Fixed problem with no annotation and duplicated lines in ivar_variants_to_vcf_script

## Description

BUG fixes in `ivar_variants_to_vcf` script.

- Ivar generates duplicated lines when using some gff that makes overlapping annotations for the same variant position. Now duplicated positions due to annotation are ignored for vcf format conversion. 
-  Positions in intergenic areas are not annotated in ivar tsv file  (NA in codon REF/ALT column). `ivar_variants_to_tsv` skips merge codons for this positions. 

## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
  - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
  - [ ] If necessary, also make a PR on the nf-core/viralrecon _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [x] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cef81a8b7db3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.