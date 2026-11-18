# Issue

**Title:** Feature/subworkflow refactor

## Description

## Subworkflow refactor (`feature/subworkflow-refactor`)

Refactored `workflows/mettannotator.nf` into three independent, reusable subworkflows. No pipeline behaviour is changed.

### New subworkflows

| Subworkflow | Modules |
|---|---|
| `subworkflows/gene_calling.nf` | LOOKUP_KINGDOM, PROKKA (standard + compliant), RENAME_CONTIGS, BAKTA_BAKTA, NORMALIZE_ENSEMBL_GFF, GFF_TO_GBK |
| `subworkflows/fast_annotation.nf` | QUAST, PSEUDOFINDER, PSEUDOFINDER_POSTPROCESSING, CRISPRCAS_FINDER, EGGNOG_MAPPER_ORTHOLOGS, EGGNOG_MAPPER_ANNOTATIONS, AMRFINDER_PLUS_GET_SPECIES_NAME, AMRFINDER_PLUS, AMRFINDER_PLUS_TSV_POSTPROCESSING, AMRFINDER_PLUS_TO_GFF, DEFENSE_FINDER, DETECT_TRNA, DETECT_NCRNA, GECCO_RUN, ANTISMASH, ANTISMASH_TO_GFF, ANTISMASH_SUMMARY, DBCAN |
| `subworkflows/slow_annotation.nf` | ADD_TAXID_TO_PROTEIN_FASTA, INTERPROSCAN, UNIFIRE, SANNTIS |


## PR checklist

- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/ebi-metagenomics/mettannotator/tree/master/.github/CONTRIBUTING.md)
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d8df208786f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.