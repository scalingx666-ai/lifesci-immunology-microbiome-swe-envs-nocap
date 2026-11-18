# Issue

**Title:** Export GPU binary without saving build layers for CI

## Description

## Summary

The Azure GPU jobs ran out of disk space on the ubuntu-26.04 image, which stores image layers twice. The Dockerfiles kept the whole build directory in the image only to copy out one binary.

Build in a separate stage and export only the mmseqs binary with docker build `--output`. Skip the unit tests in these builds, since the GPU jobs never run them and linking them statically against `libmarv` takes extra disk space.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41e1665d7ddc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.