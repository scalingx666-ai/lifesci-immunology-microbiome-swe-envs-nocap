# Issue

**Title:** SINTAX for all databases supported by DADA2

## Description

<!--
# nf-core/ampliseq pull request

Many thanks for contributing to nf-core/ampliseq!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
-->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] If you've fixed a bug or added code that should be tested, add tests!
- [x] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/ampliseq/tree/master/docs/CONTRIBUTING.md)
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Description

SINTAX could only use databases that are distributed in VSEARCH format (COIDB, UNITE).
`--sintax_ref_taxonomy` now accepts every database that `--dada_ref_taxonomy` accepts, plus MIDORI2-CO1, including the versioned keys.

Each new entry in `sintax_ref_databases` reuses the files and format script of the DADA2 entry and appends `bin/taxref_reformat_dada2_to_sintax.sh`.
That script converts the assignTaxonomy fasta (`>A;B;C;`) to a VSEARCH fasta (`>s1;tax=d:A,k:B,p:C`).
VSEARCH 2.31.0 accepts the rank letters `d,k,p,c,o,f,g,s,t`, so up to nine ranks work, which PR2 needs.
Species are only assigned where the DADA2 training fasta holds them (not for RDP, for example).

Tested by extending the Diat.barcode test to also run SINTAX and compare its species with the DADA2 result.
The converter was also run on the real DADA2 files of SILVA 138.2, RDP 18, PR2 5.1.0, SBDI-GTDB R11-RS232-1 and Zehr-nifH 2.5.0, and PR2 through VSEARCH.
Only `tests/diatbarcode.nf.test` was run locally; the full test suite is left to CI.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4810a1121f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.