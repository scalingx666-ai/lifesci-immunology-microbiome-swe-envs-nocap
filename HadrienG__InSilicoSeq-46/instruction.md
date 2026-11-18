# Issue

**Title:** Python 2 fixes + insert size distribution

## Description

This PR addresses the bugs from #45 (and more):

Python2 related:
* `zip(*args.ncbi, *args.n_genomes)` not supported. Changed syntax.
* changed `import http`to `import http.client` to catch the incomplete download/N exceptions
* insertions are `str` and not unicode anymore

Not python2 related:
* iss does not skip a genome if its length is shorter than the random insert size drawn from the model. Produces a random insert size within acceptable limits instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ff8bd27691db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.