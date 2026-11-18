# Issue

**Title:** Enable building on any 64-bit little-endian architecture

## Description

Using the [SIMD Everywhere (SIMDe) library](https://github.com/simd-everywhere/simde).

We are using this patch on Debian to build vsearch for RISCV64 and other architectures

This PR is a workaround for  until a dedicated RISCV64 Vector implementation is added

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e79adfd5c77e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.