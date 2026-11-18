# Issue

**Title:** Skip ancient DNA validation for long-read assemblies

## Description

().

With `--ancient_dna`, long-read assemblies (Flye, metaMDBG) went through ancient DNA validation: they were mapped against for pyDamage and damage correction, and binning used their "corrected" contigs. Damage validation is meant for short-read data, so long-read assemblies are now excluded.

## Changes

- Long-read assemblies are no longer passed to `BINNING_PREPARATION_FULL`, so they skip pyDamage, freebayes and consensus recalling. Short-read and hybrid (SPAdesHybrid) assemblies are unchanged.
- Binning uses the damage-corrected contigs for assemblies that have them, and the `--min_contig_size`-filtered contigs for the rest. Before, binning joined only on corrected contigs, so excluding long-read assemblies from validation would have dropped them from binning.
- `SUMMARISE_PYDAMAGEBINS` is skipped when there are no pyDamage reports, which now happens in long-read-only runs with `--ancient_dna`. Bins of long-read assemblies get empty pyDamage columns in `bin_summary.tsv`.

## Testing

- `test_single_end` (the aDNA test) passes with an unchanged snapshot.
- `test_longreadonly` with `--ancient_dna` completes: Flye and metaMDBG assemblies are binned, pyDamage/freebayes do not run, and `bin_summary.tsv` is produced.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`). The only failure is `files_unchanged` for `assets/nf-core-mag_logo_light.png`, also present on `dev`.
- [x] Ensure the test suite passes.
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f090a400ec42`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.