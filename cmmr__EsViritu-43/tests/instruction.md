# Issue

**Title:** taxonomy adjuster

## Description

adding post-consensus assembly to ref mapping step and parsing to adjust taxonomy calls.
1. align consensus genomes back to references.
2. Collate alignment stats by Assembly.
3. Determine best taxID. Use LCA when there is a tie.
4. Adjust taxon for the `detected_virus.info.tsv` and `.detected_virus.assembly_summary.tsv` outputs.
5. Propagate tax call to `tax_profile.tsv`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df90f449b487`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.