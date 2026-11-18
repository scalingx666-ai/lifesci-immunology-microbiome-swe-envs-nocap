# Issue

**Title:** arda 2.6.1 — `arda igblast` works from a pip install

## Description

`arda igblast` resolved IgBLAST only through `<project>/bin`, populated by `setup.sh`. A plain
`pip install arda-mapper` has no checkout and never runs it, so **every** invocation failed —
and that is the command producing the gold standard the benchmark is scored against. A
27-dataset panel run on a freshly deployed 2.6.0 returned no truth file on all 27 samples while
every tool run in the same job succeeded.

The error named the wrong thing: `IgBlastError: IgBLAST ships no internal annotation for
organism 'human'` — a missing *install* surfacing as a missing *data file* inside a present one.

IgBLAST is now fetched from NCBI on first use, exactly as mmseqs already was. Atomic and
concurrency-safe (sibling staging dir, one `os.replace`, readiness gated on a marker written
last, not on `igblastn.exists()`).

Verified end to end from a wheel install with no IgBLAST on the machine: fetches 1.22.0 and
writes 660 AIRR rows. 414 tests pass, ruff clean.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4627468cf22e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.