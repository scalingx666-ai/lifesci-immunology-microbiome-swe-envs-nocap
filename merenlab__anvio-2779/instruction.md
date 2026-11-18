# Issue

**Title:** Sra download rule fixes

## Description

While looking into adding SRA downloads to the metagenomics workflow, I ran into a few issues in the `sra_download` workflow. They're unrelated to that work, so here they are on their own PR :)

## One accession could steal another's reads
The step that compresses FASTQ files searched for them using a wildcard. But SRA accessions vary in length, so `SRR1195143*` also matches files belonging to `SRR11951439`. When that happens, two jobs grab the same file and one accession ends up missing.

Now each job compresses only the exact file names that belong to it.

## Downloaded `.sra` files were never deleted

The config has a `Remove_unzipped_SRA_files` option, and it's on by default but the value was read and then **never used**. Every downloaded archive stayed on disk for the whole run, which adds up fast with a long accession list.

The option now does what it says. Only the archive is deleted, so re-running the workflow still doesn't re-download anything.

## The checksum step crashed on some accessions

Verifying a download meant asking NCBI for its checksum. For suppressed or access-restricted accessions, NCBI answers with something different and the workflow died with a raw Python error and no explanation.

Now it reads the response properly and tells you what went wrong. If NCBI simply doesn't report a checksum, you get a warning and the workflow keeps going instead of stopping.

## Also
The `{accession}` wildcard was too wild, meaning it could match anything at all (including `/`). It's now limited to the accessions you actually asked for.

## Testing

`anvi-self-test --suite workflow-sra-download` now checks its own results rather than just checking that nothing crashed. It confirms the expected files exist, that no uncompressed leftovers or `.sra` archives remain, and that a second run doesn't re-download anything.

It also includes A TRAP FILE designed to be caught by the old wildcard search. That fails on `master` and passes here, so the first bug can't quietly come back.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `645096215e98`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.