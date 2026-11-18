# Issue

**Title:** Expose option to set `kmer_probe_map_k` parameter

## Description

This adds a `--kmer-probe-map-k` argument, which specifies the k-mer length used when constructing a map of k-mers to probes.  (In particular, CATCH tries to determine a suitable k-mer length using this value as a lower bound; if it cannot, it takes a randomized approach and uses this value as the k-mer length.)

This is useful when designing short probes (e.g., meant to be primers), in which case the default k-mer length may be too short relative to the probe to find mappings of the probes to the target sequence.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af7929e8d7c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.