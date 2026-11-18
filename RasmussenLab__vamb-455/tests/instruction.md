# Issue

**Title:** Refactor cluster printing

## Description

This PR picks up some of the remaining work from Elek's recent refactoring of cluster printing. It simplifies the logical flow of contig printing by reducing the number of functions.

The logic is more clear about when printing happens: It now separates the cluster writing into two functions: One clusters and writes the associated files while clustering. Another function, used e.g. when reclustering, merely writes the files.

This commit also:
* Fixes a bunch of type errors, making the code pass typecheck
* More thoroughly encodes the state into the type system: i.e. if arguments A and B are needed together, or not at all, they are condensed in a single variable of type Option[tuple[A, B]].

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0056e2daf9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.