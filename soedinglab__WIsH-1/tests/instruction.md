# Issue

**Title:** updated readme - fixed problems with the build system

## Description

:tada:

* added instructions how to compile on MacOS
* removed `#define OPENMP` from main.h
* statically cast `fin.tellg()` from `std:fpos` to `static_cast<unsigned long>(fin.tellg())` to make it compile on clang. Should be somewhat safe, I guess?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb2234796f9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.