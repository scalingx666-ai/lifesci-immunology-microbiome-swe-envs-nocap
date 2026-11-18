# Issue

**Title:** Add minibwa as a mapper

## Description

Integrate minibwa (https://github.com/lh3/minibwa) as a `-p minibwa` mapping option, modelled on the existing BWA integration since minibwa is BWT-based and requires a pre-built index.

- Index: `minibwa index [-t N] <ref.fa> <out.prefix>` (prefix is a positional argument, not `-p`), producing `.l2b` and `.mbw` files.
- Map: `minibwa map -t N <idx> <r1> [r2]`.
- Version check uses the `minibwa version` subcommand (e.g. `0.2-r370`); `minibwa --version` is not recognised.
- Reject `--interleaved` input: minibwa has no interleaved-pairing option.

Add minibwa to the pixi environment for linux-64 and osx-64 (it is not available on osx-arm64). Remove dashing, which hard-pins zlib<1.3 and so conflicts with minibwa's libzlib>=1.3.2; dashing was only an optional galah precluster method (skani is the default).

Add assert_cli tests for coupled-read mapping and interleaved rejection.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5222aba4ab10`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.