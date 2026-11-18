# Issue

**Title:** Make --resume safe and on by default

## Description

Resolves the request to have resume active by default (see issue #87): the same command can be resubmitted after a failed or killed job without editing the job script.

### What changes
- **`--resume` is now the default.** If there is nothing to resume, Binette logs an info message and starts from scratch instead of failing. Use `--no-resume` to recompute everything.
- **Resuming checks that it is the same run.** A `temporary_files/checkpoint.json` records fingerprints of the inputs (contig sequences, bin sets, `--proteins`, CheckM2 DB) and checksums of the intermediate files. Proteins and DIAMOND results are reused only if they match and are intact.
- **Interrupted jobs can't leave half-written files.** Protein and DIAMOND outputs are written to a temporary file and moved into place only when complete.
- **A completed run is not redone.** Rerunning with the same inputs and parameters exits immediately. Changing only selection parameters (`--min_completeness`, `-w`, `--prefix`…) reuses proteins and DIAMOND. Toggling `--no-write-fasta-bins` doesn't trigger recomputation.
- **New `--force` flag.** Binette now refuses an output directory that holds results from *different inputs* (or from an older version that can't be verified). `--force` overrides this. This is likely solving issue #95.
- **`coding_density` is kept on resume.** Resumed runs give the same results as fresh runs.

### Others
- README / usage docs are updated.

Implemented with help from Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `989088407625`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.