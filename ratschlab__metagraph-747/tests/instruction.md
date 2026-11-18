# Issue

**Title:** Update the SDSL fork to current upstream

## Description

This moves the SDSL fork to a commit that merges upstream xxsds/sdsl-lite master (e20e202d). The fork had fallen 20 commits behind, mostly our own PRs that eseiler reviewed and merged there.

The fork now takes upstream's code for the hybrid vector, the packed `int_vector` iterators and the shared word helpers. It keeps the lab `int_vector` header and its unaligned reads, so existing index files load unchanged. The RRR and `select_support_mcl` layouts are also unchanged.

Two behaviour changes come with upstream's code. Const element access on 8-, 16-, 32- and 64-bit `int_vector`s returns a reference again, because upstream's hybrid vector keeps references to its header words. `int_vector_mapper` now rejects a missing file also in plain mode.

The updated SDSL needs GCC 13 or newer. GCC 11 and 12 reject its hidden-friend iterator operators (a GCC limitation fixed in GCC 13). So CI now tests GCC 13 only, the Docker build stage moves to Ubuntu 24.04 with GCC 13, and the installation docs state the minimum.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ef979827505f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.