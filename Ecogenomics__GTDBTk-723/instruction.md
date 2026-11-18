# Issue

**Title:** Fix Parallel hanging on Python 3.14 and macOS

## Description

Hi,

GTDB-Tk hangs on Python 3.14. At "Running Prodigal" a child process dies with

```
AttributeError: 'Parallel' object has no attribute '__process_manager'
```

and the main process waits for it forever. This is the error in #683, and I believe it's why the bioconda recipe caps Python below 3.14 (bioconda/bioconda-recipes#61837).

The cause is in `biolib_lite.Parallel`, which passes its two private methods, `__producer` and `__process_manager`, to `mp.Process`. That works with `fork`, but with `spawn` and `forkserver` the target has to be pickled, and Python pickles a bound method by its unmangled name, so the child can't find it. Python 3.14 changed the default on Linux from `fork` to `forkserver`, which is why this shows up now. macOS has defaulted to `spawn` since Python 3.8, which is #619 and how I ran into it.

The fix is just renaming the two methods to `_producer` and `_process_manager`. Nothing else in the package refers to them. I've also added a small test that runs `Parallel` under each start method. It times out under `spawn` and `forkserver` without the fix.

I've tested it with 2.8.0 on the mock database (`classify_wf -x gz --place_species -f`):

- Linux (x86-64), Python 3.14: hangs as released (I killed it after 10 minutes), finishes in 30 s with the fix.
- macOS (Apple silicon), Python 3.13, with pplacer 1.1.alpha23 since alpha19 has no arm build: hangs as released, finishes with the fix, and gives the same summary as forcing `fork`.

Let me know if you'd like anything done differently.

Kind regards, Carl

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e552e6e79bbb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.