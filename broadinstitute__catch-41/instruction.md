# Issue

**Title:** Improve handling of the case when there are no candidate probes

## Description

There may be some valid cases where there are no candidate probes. For
example, if genomes are clustered and `--small-seq-skip` is set, one
cluster may contain short genomes that are all skipped -- and thus and
the cluster has no genomes and therefore no candidate probes. This will
cause an error because `kmer_probe_map` would be empty. This PR allows
clusters/groupings of genomes to have no candidate probes, and for CATCH
to proceed in that case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8d42266dd3a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.