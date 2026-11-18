# Issue

**Title:** Add --max_contig_size to filter long contigs before binning

## Description

, as suggested by @prototaxites: an optional maximum contig size for binning, to discard host or other eukaryotic contigs, which are usually much longer than prokaryotic ones.

## Changes

- New `--max_contig_size` parameter (no limit by default). It is applied by the same `seqkit seq` step as `--min_contig_size`, before the read mapping for binning, so all binners see the same contigs.
- ALE, DeepMAsED and ancient DNA validation are not affected, as they use the unfiltered assemblies.
- The pipeline stops with an error if `--max_contig_size` is lower than `--min_contig_size`.

## Testing

- `-profile test --max_contig_size 50000` completes, with `seqkit seq --min-len 1500 --max-len 50000` and the longest contigs removed.
- `--max_contig_size 100` fails at parameter validation.
- No test profile sets the new parameter, so snapshots are unchanged.

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [x] Make sure your code lints (`nf-core pipelines lint`). The only failure is `files_unchanged` for `assets/nf-core-mag_logo_light.png`, also present on `dev`.
- [x] Ensure the test suite passes.
- [x] Usage Documentation in `docs/usage.md` is updated.
- [x] `CHANGELOG.md` is updated.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7fbb2153e338`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.