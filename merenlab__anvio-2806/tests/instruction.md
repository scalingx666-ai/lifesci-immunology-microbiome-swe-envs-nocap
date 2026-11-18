# Issue

**Title:** Db hash handling

## Description

With this PR, every contigs database will carry a hash value in its `self` table under the key `contigs_db_hash`, which will look like this (24 digits by default, good luck, universe): `0a1b2c3d4e5f6789blahblah`.

Every anvi'o database that is generated from a contigs database (such as a `profile-db`, a `genes-db`, or a `structure-db`) keeps a copy of this value so anvi'o can make sure you are not accidentally using them together with a contigs database they have nothing to do with.

*This hash is deterministic* as anvi'o will compute it from the content as well as the structure of the database itself (i.e. the names and the sequences of its contigs, the split boundaries, the gene calls, etc). Which means running `anvi-gen-contigs-database` twice on the same `contigs-fasta` with the same parameters will give you two databases with the same hash. Thus, if you have accidentally delete a contigs database, regenerating it the very same way will make it compatible with the profile databases you had generated from the original one, and will contribute to `contigs-db` provenance. Conversely, anything that would invalidate those downstream databases (a different split length, a different gene caller, or of course different sequences) will change the hash, and anvi'o will tell you that your databases are not compatible.

Things that are added to a contigs database after its creation, such as functional annotations, HMM hits, or taxonomy, do not change its hash, since none of them invalidate anything that is linked to it.

Adresses #2803.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa24a9c51c1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.