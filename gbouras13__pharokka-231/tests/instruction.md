# Issue

**Title:** V1.2.0

## Description

* Adds the functionality of mapping each contig against the INPHARED database using mash (https://github.com/RyanCook94/inphared). The top hit for each contig (under a maximum mash distance threshold of 0.2) is kept.
* Replaced prodigal with pyrodigal as it is being actively maintained and used by bakta.
* Adds --citation.
* Adds checks for dependencies.
* Adds --terminase terminase mode to re-orient a single contig phage to begin with a certain orientation and coordinate (most commonly, the large terminase subunit). With this, you must also specify --terminase_strand the strand of the terL gene and --terminase_start the start coordinate.
* All locus tags end with 4 digits (trailing zeros) in order to play nice with vConTACT2 and start with 1 not 0.
* In meta mode, the locus tags now begin with the contig header, not a random string (or chosen prefix).
* Updates .tbl output so it is in a format to automatically be accepted by NCBI Bankit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fde1f85a83bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.