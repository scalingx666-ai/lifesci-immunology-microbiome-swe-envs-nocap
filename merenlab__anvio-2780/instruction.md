# Issue

**Title:** rename the sra_download FASTQ output directory

## Description

The `sra_download` workflow downloads sequencing reads and puts them in a directory called `02_FASTA`. WRONG DIR NAME.

It's now `02_FASTQ`, with the config key renamed from `FASTAS` to `FASTQ_DIR` so it matches the `*_DIR` naming every other directory key uses.

## Nothing breaks for existing users

The output directory is where the expensive part of this workflow lives. If anvi'o started looking in a new directory and didn't find the reads you already downloaded, it would download all of them again. So:

- **If your config file has an `output_dirs` section** (`--get-default-config` command always writes one), anvi'o reads the old `FASTAS` key, keeps using the directory you already had, and prints a note asking you to rename the key when convenient. Your runs continue exactly where they left off.
- **If it doesn't**, and anvi'o spots an `02_FASTA` directory from an earlier run, it warns you before doing anything and tells you the two ways to keep using it.

New configs generated from here on get `02_FASTQ`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3947bfa41f05`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.