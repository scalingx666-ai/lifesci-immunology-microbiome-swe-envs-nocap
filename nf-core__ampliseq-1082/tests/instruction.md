# Issue

**Title:** Keep non-rank content out of the QIIME2 taxonomy string

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
- [x] Make sure your code lints (`nf-core pipelines lint`).
- [ ] Ensure the test suite passes (`nextflow run . -profile test,docker --outdir <OUTDIR>`).
- [x] `CHANGELOG.md` is updated.

## Description

The taxonomy string imported into QIIME2 should hold taxonomic ranks and nothing else.
Two independent defects put other content there, both present on `dev`.

A rank that is empty for every ASV was rendered as the literal taxon `NA`.
`read.table` infers a column's type from its contents, and a column that is empty throughout has nothing to infer from, so it is typed `logical` and filled with `NA`, which `paste` writes as the four-character string.
The trigger is a whole column being empty, so it is all-or-nothing per run: a dataset where `assignTaxonomy` resolves no ASV to species level gets `;NA` appended to every ASV.

`SH` and `BOLD_bin` were treated as ranks.
Both are sequence-cluster identifiers that databases declare among their `taxlevels`, so they arrive as ordinary columns and were joined into the string.
QIIME2 emits one `level-N` file per segment it is given, so an `--addsh` run produced a `level-8.csv` whose "rank" was a column of SH identifiers, and the rank-collapsed outputs at that level were meaningless.

Neither defect fails a run; both silently produce a wrong or extra taxon.

### What changed

`bin/parse_dada2_taxonomy.r` now reads every column as character, with `na.strings` emptied so an empty field is not turned back into `NA`, and excludes `SH` and `BOLD_bin` alongside the non-rank columns it already excluded.
That matches `bin/sbdiexport.R`, which already maps both to `otu` rather than to a rank.

### Verification

`tests/sintax.nf.test` carries an SH column, so its snapshot loses `level-8.csv` and `level-8.jsonp` from the barplot and both `barplot_average` directories.
Nothing else in that snapshot moves.
The suite passes, and an explicit assertion now states the expectation instead of leaving it as an md5 delta.

The empty-rank case has no profile that reproduces it, since no test dataset leaves a rank empty throughout, and giving it one would mean a new dataset and database pairing for a single `read.table` argument.
It is verified by running the script directly against tables of that shape, covering empty and populated ranks with and without the identifier columns.

`prek`, `nf-core pipelines lint` (0 failures) and `nextflow lint .` on 26.04.0 and 26.04.6 are clean.
The `default`, `vsearch_lca` and `pplace` profiles have not been run locally yet, hence the unticked box above.

.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01PYuhWC4HE6BP63fnsVQZHN

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d4f0a18a08b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.