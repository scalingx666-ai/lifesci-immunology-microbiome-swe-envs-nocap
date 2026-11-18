# Issue

**Title:** Use the BSD rewrite of dac_vector_dp for count annotations

## Description

Count annotations now use a BSD rewrite of `sdsl::dac_vector_dp`, the class proposed upstream in xxsds/sdsl-lite#194. The submodule moves to the fork commit that carries it.

The class keeps its template signature and serialized structure. Existing count annotations load unchanged, and annotations written by the new class load with older binaries.

Measured against master on one exclusive Euler node (EPYC 9654), 128 count columns built from 1.4 Gbp of synthetic reads, medians of 3 runs:

| step | master | this PR |
|---|---|---|
| `transform_anno --anno-type int_brwt` | 26.2 s, 1.68 GB | 21.0 s, 1.27 GB |
| `transform_anno --anno-type row_diff_int_brwt` | 6.38 s | 5.82 s |
| `query --query-mode counts`, int_brwt, 1 thread | 3.59 s | 3.64 s |
| `query --query-mode counts`, row_diff_int_brwt, 1 thread | 1.73 s | 1.74 s |
| int_brwt file size | 228.4 MB | 226.7 MB |

Query outputs are identical, also when each binary reads the other's annotations.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1f785fcfd55`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.