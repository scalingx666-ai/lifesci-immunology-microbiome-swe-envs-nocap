# Issue

**Title:** KGML intermediate chain removal optimization

## Description

The KGML network walker that analyzes KEGG pathways walks reaction chains from compounds in the pathway (by default, all compounds), which can result in chains that were walked from certain compounds that are subchains of superchains from other compounds. The walker has an attribute, `keep_intermediate_chains`, which, when `False`, identifies and removes subchains from returned chains. `remove_intermediate_chains` did not have an efficient implementation, causing runtime bottlenecks for complex pathways in larger genomes. The speed up here 1) precomputes chain information instead of rebuilding in pairwise comparisons of potential subchains and superchains, and 2) indexes chains under consideration by consumption vs. production type (`is_consumed` attribute) and first KGML compound ID, since a superchain must contain a subchain's compounds in the same order.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1254f3ee5cb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.