# Issue

**Title:** Add Logan and Logan50 protein databases to DB downloader

## Description

Adds the Logan protein sets (https://github.com/IndexThePlanet/Logan/blob/main/Proteins.md) to `mmseqs databases`:

| Name               | Download (zstd) |
|--------------------|-----------------|
| `Logan-human`      | ~283 GiB        |
| `Logan-nonhuman`   | ~1.8 TiB        |
| `Logan50-human`    | ~5.5 GiB        |
| `Logan50-nonhuman` | ~253 GiB        |

Human- and nonhuman-associated proteins are separate databases, since they are searched separately and differ a lot in size.

Logan is only distributed as zstd-compressed FASTA, which `createdb` cannot read. The new `FASTA_ZSTD_LIST` input type streams `zstd -dc` into `createdb stdin`, so the uncompressed FASTA never hits the disk. This requires `zstd` in `PATH`, which is checked before downloading. If decompression or `createdb` fails, the partial database is removed so a rerun does not skip `createdb`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a0e39f2ea28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.