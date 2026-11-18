# Issue

**Title:** disable default CXXFLAGS

## Description

Hi @torognes , I've disabled the default `CXXFLAGS` which were `-O2 -g`. Before that, all objects were built using the CXXFLAGS provided in src/Makefile.am **PLUS** the `-O2 -g` flags. I'm not sure what the precedence is when using different -O flags and perhaps -O3  still had precedence, but for clarity I've removed the defaults.

Note that now both libcpu_sse2.a and libcpu_ssse3.a are _not_ compiled with any optimization flags (not sure if this was intentional). Prior this PR, both were compiled with the defaults (`-O2 -g`).
The clean way to add optimization flags now would be to alter the `libcpu_sse2_a_CXXFLAGS` and `libcpu_ssse3_a_CXXFLAGS` in `src/Makefile.am`.

Tomas

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `406c7431980f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.