# Issue

**Title:** Centralize posix_madvise wrapper with errno-aware severity

## Description

## Problem

Five call sites in MMseqs2 log every `posix_madvise` failure at `Debug::ERROR` severity, even though `posix_madvise` is a purely advisory API and every site falls through to continue execution.

On ARM64 kernels with 64KB pages (e.g. NVIDIA Grace, Apple Silicon under some configs), a benign tail-page alignment mismatch on `mmap`'d databases produces user-visible

```
posix_madvise returned an error (touchMemory)
```

lines via stdout/stderr capture in downstream services (e.g. mmseqs `gpuserver`). This suggests a fault where none exists and is confusing for operators triaging real failures.

The same call sites also discard `errno`, so when a real I/O problem does occur (`EIO`, `EBADF`, `ENOMEM`) there is no way to tell it apart from the benign cases.

## Change

Introduce `Util::madviseLogged(addr, len, advice, context)` in `commons/Util.{h,cpp}` which:

- returns `0` when `len == 0` or `HAVE_POSIX_MADVISE` is undefined
- on failure, logs `strerror(rc)` with the named advice and a caller-supplied context string
- chooses severity by category:
  - `SEQUENTIAL` hints — always `WARNING` (pure readahead hint, never functional)
  - `WILLNEED` + `EINVAL` — `WARNING` (alignment / VMA-type edge case, manual touch loop still prefaults)
  - `WILLNEED` + other errno — `ERROR` (`EIO` / `EBADF` / `ENOMEM` indicate real problems)

Fallback `POSIX_MADV_*` macros are provided in `Util.h` so call sites compile cleanly when `HAVE_POSIX_MADVISE` is undefined; the helper is a no-op in that build configuration.

All five sites are refactored onto the helper:

- `src/commons/Util.cpp` (`touchMemory`)
- `src/commons/DBReader.cpp` (`setSequentialAdvice`)
- `src/linclust/KmerIndex.h` (`KmerIndex` load)
- `src/linclust/kmermatcher.cpp` (`mergeKmerFilesAndOutput`)
- `src/prefiltering/Prefiltering.cpp` (`mergeTargetSplits`)

The `#ifdef HAVE_POSIX_MADVISE` guards previously wrapping each site are now consolidated inside the helper.

## Behavior change

- No functional change.
- Severity classification changes as described above.
- Log message format changes: now includes the advice name and `strerror()` text.

  Before:
  ```
  posix_madvise returned an error (touchMemory)
  ```
  After (WILLNEED + EINVAL on a 64KB-page ARM64 kernel):
  ```
  posix_madvise(WILLNEED) failed for touchMemory: Invalid argument
  ```

## Reproduction of original warning

Run any mmseqs workload that loads a database via `touchMemory` (e.g. `mmseqs gpuserver`) on an ARM64 host with 64KB pages and a database whose mapped length is not a multiple of the page size. The previous build emits `Debug::ERROR`; this build emits `Debug::WARNING` with errno context.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18cc7493f392`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.