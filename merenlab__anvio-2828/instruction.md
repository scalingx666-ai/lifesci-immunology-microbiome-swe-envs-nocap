# Issue

**Title:** Make `anvi-draw-kegg-pathways` unified and group map summaries independent of Python's hash seed

## Description

#2825 passed a `set` of accession strings as `entry_keys` for 'unified' maps with a sample summary and for the maps of individual groups. Map entries are colored in the order of `entry_keys`, and a set of strings is ordered by Python's hash seed. A color keeps the priority of the last entry given it. On global and overview maps, derived compound colors average those priorities. So two runs of the same command could draw different maps.

This PR builds `entry_keys` as an ordered `dict.fromkeys`, in first-appearance order. A grouped 'unified' map takes the samples group by group. This is the order from before #2825. The `entry_keys` docstring now says when the order matters.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fca459eba868`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.