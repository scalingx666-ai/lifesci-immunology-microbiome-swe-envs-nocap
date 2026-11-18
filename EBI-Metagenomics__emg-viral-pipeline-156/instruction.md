# Issue

**Title:** Fix/spaces in contignames issue

## Description

- Made coordinates `int` instead of `float`
- removed `postprocess` subwf (it was only restore). Added "short" names to original fasta and category fasta.
- changed `restore` function to add prophage metadata after contig name (before space) to make it unique.
Example,
`ERZ12593051.63 NODE_63_length_59433_cov_64.962579` would be `ERZ12593051.63|prophage-6654:18314`
it was `ERZ12593051.63 NODE_63_length_59433_cov_64.962579|prophage-6654:18314`
**checkV** takes only contig name before space and complained for duplicates if one contig represented twice but with different propahge regions in metadata

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8346a4d55cab`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.