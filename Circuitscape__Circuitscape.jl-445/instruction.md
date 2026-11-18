# Issue

**Title:** Migrate from Distributed.jl to Julia threading

## Description

## Summary

Depends on #444 (pardiso-extension).

- Replace `pmap`/`addprocs`/`SharedArrays` with `Threads.@spawn` and plain arrays
- Parallelism now uses Julia's native threading (`-t` flag) instead of spawning separate processes
- Remove `Distributed` and `SharedArrays` dependencies
- Remove `GC.gc()` call from solve loop (causes stop-the-world pauses across threads)

## What changed

- `pmap(f, ...)` → `fetch.(map(x -> Threads.@spawn(f(x)), ...))` in 3 call sites (AMG pairwise, CHOLMOD pairwise, one-to-all)
- `SharedMatrix`/`SharedVector` → plain `Matrix`/`Vector` in `Cumulative` struct
- `mycsid()` uses `Threads.threadid()` instead of `myid()`
- `nprocs()` → `Threads.nthreads()` throughout
- `myaddprocs` is now a no-op (threads are set via `-t` flag)

## Usage

```bash
julia -t 4 -e 'using Circuitscape; compute("job.ini")'  # 4 threads
```

Or set `parallelize = True` in the INI file (backward compatible).

## Test plan

- [ ] All tests pass on all platforms
- [ ] Parallel tests produce correct results with multiple threads

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7925edb899e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.