# Issue

**Title:** Use orientation-preserving SSHash lookup for BASIC graphs

## Description

BASIC SSHash graphs now build with strand-specific heavy-bucket keys. Forward-only lookups no longer scan heavy minimizer buckets for the other strand.

The SSHash pin moves to  on `metagraph/orientation-preserving-lookup`. It adds the opt-in `preserve_orientation` build option from jermp/sshash#108 to the current pin (f411a6e). MetaGraph enables it for BASIC graphs only.

Format:
- BASIC graphs are written as SSHash v7. Binaries with the previous SSHash cannot read them.
- Canonical and primary graphs stay v6, byte for byte.
- Existing v6 graphs of all modes still load. Old BASIC graphs keep the slower lookup until rebuilt.
- The v7 layout matches jermp/sshash#108, so these graphs stay readable if that PR merges unchanged.

For GnomAD k41 (23.05 billion k-mers), BASIC construction took 1 h 53 min with an earlier fork version of this lookup (2079fe7). The previous pin was still building after 22 h 17 min. These were single runs on different Euler nodes, both with 32 threads.

Prepared with AI assistance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9a5dc06f999`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.