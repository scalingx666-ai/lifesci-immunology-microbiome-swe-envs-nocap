# Issue

**Title:** Fix out-of-bounds read in createAsciiSubMat (segfault in rescorediagonal ungapped scoring)

## Description

## Summary

`SubstitutionMatrix::createAsciiSubMat` builds its ASCII-indexed lookup table for bytes 0–122 (`'z'+1`), but `DistanceCalculator.h`'s ungapped scoring functions (`computeSubstitutionDistance`, `computeSubstitutionStartEndDistance`, `computeGlobalSubstitutionStartEndDistance`, `computeWindowQualitySubstitutionStartEndDistance`) index it with raw, untranslated byte values up to 255 and never bounds-check. Any byte ≥123 reads a garbage row pointer past the end of the table and segfaults on dereference. This is the crash reported in #866 ("Ungapped alignment step died" / "Search died") and looks like the same call site as #323.

This fixes it by widening the table to the same domain `aa2num` already safely maps (`setupLetterMapping`'s `default:` case sends every unrecognized byte to `'X'`), so no new out-of-bounds access is introduced and behavior for valid sequence data is unchanged.

## Root cause

Backtrace on a debug build (`-DCMAKE_BUILD_TYPE=Debug`), replaying the crashing `rescorediagonal` invocation under gdb:

```
Program received signal SIGSEGV, Segmentation fault.
0x00005555556340e8 in DistanceCalculator::computeSubstitutionDistance<char> (seq1=0x7ffff4c62169 "", seq2=0x7ffff4c62169 "", length=591, subMat=0x5555564fe920, globalAlignment=false) at src/alignment/DistanceCalculator.h:28
#1  DistanceCalculator::ungappedAlignmentByDiagonal<char> (..., diagonal=0, ...) at DistanceCalculator.h:129
#2  DistanceCalculator::computeUngappedAlignment<char> (...) at DistanceCalculator.h:106
#3  doRescorediagonal(...)._omp_fn.0 () at src/alignment/rescorediagonal.cpp:275
```

`seq1`/`seq2` (self-comparison, `length=591`) contain a literal `|` (`0x7C` = 124) at two positions in the 591-byte comparison window — one past the old table's last valid index (122). `subMat[124]` reads 2 slots past the end of the 123-element `matrix` array; the resulting fault address matched neither the heap, the substitution table, nor the mmap'd sequence DB — consistent with dereferencing a garbage pointer read from past the array.

## Reproducer

The current default pipeline (`--linclust-version 2`, `align2clust`) no longer calls `rescorediagonal`, so reproducing on current `master` needs the legacy path:

```
mmseqs easy-cluster in.fasta out tmp --min-seq-id 0.7 --threads 1 -c 0.8 --cov-mode 0 --linclust-version 1
```

Before this fix: `Segmentation fault (core dumped)` / `Error: Ungapped alignment step died` / `Error: linclust died` / `Error: Search died`, 100% reproducible on Ubuntu 24.04.4 / glibc 2.39.

## Validation

- With this fix, the same `--linclust-version 1` command completes (149,739 sequences -> 32,234 clusters, exit 0) instead of crashing.
- Reran `easy-cluster` with the default pipeline (`--linclust-version 2`, unaffected by the bug) before and after this change on the same input: `cluster.tsv` is byte-identical, so this doesn't change results for the code path most users hit today.

## Test plan

- [ ] `--linclust-version 1` no longer segfaults on an input containing non-alphabet bytes
- [ ] Default pipeline output is unchanged (covered above; happy to add as an automated regression test if there's a preferred place for it — didn't see an existing test harness for `rescorediagonal` specifically)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c77b5afa910b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.