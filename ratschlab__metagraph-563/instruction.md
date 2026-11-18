# Issue

**Title:** Server changes: load all graphs, don't compute num_relations in stats

## Description

Improvements in server

* Computing num_relations takes up to 1 min for very large graphs that are loaded with mmap and not cached.
Now we don't report it, hence `/stats` always works instantly.

* Always keep all graphs loaded, so that they don't need to be reloaded for every query.

* Don't store copied annotation labels, which may create a large overhead for indexes with many labels

* Fixed catching exceptions thrown in worker threads, so now it reliably works with incorrect requests in multi-graph regime.

* Logging and other minor improvements

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `00945af597fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.