# Issue

**Title:** Speed up departures, arrivals, and the cumulative edgelist with C kernels and match()

## Description

and #1142. Builds on #1140 (the branch is based on `shiftvec-c`), so it shows those commits until that PR merges.

At 100k nodes EpiModel's own bookkeeping on departures and arrivals is a visible share of the step once a model carries many nodal attributes. This PR takes the four items from #1141:

- `remove_node_attr()` and `append_attr()` copy plain integer, double, logical, and character attribute vectors in one C pass each (`src/attr_kernels.c`). Vectors with attributes or of other types still go through `[` and `c()`, so the result is what base R gives. The plain-vector check is done in R because `ATTRIB()` is not part of R's C API.
- `delete_vertices()` renumbers the edgelist in one pass from a drop mask and `cumsum()` instead of sorting each column, and keeps the sort-based path for inputs it cannot vet (missing `n`, NAs, duplicates, ids out of range).
- `update_cumulative_edgelist()` matches the current edges to the open partnerships on a numeric pair key, with the `full_join` as fallback for duplicate keys or ids above 2^26.
- `remove_node_attr()` and `delete_attr()` with an empty id vector return `dat` unchanged instead of dropping every node (#1142).

The accessor change from the prototype is left to #1074. Unit tests pin each path against its base R equivalent on every attribute type (double, integer, logical, character, factor, named, Date, list), `delete_vertices()` against the sort-based path on random edgelists, and the cumulative edgelist against the join.

Pre/post on a 100k-node toy model with 100 nodal attributes (60 double, 25 integer, 10 logical, 5 character), tergmLite with arrivals and departures and the cumulative edgelist on, 30 steps, same seed. Old is the `shiftvec-c` build, new is this branch.

Equivalence: `identical()` is TRUE for the epi output, the network statistics, the complete final run state (attributes, edgelists, cumulative edgelist, `net_attr`) and the RNG state. The per-function outputs below are identical on identical inputs.

| | old ms | new ms | ratio |
|---|---|---|---|
| Whole step, `netsim()` | 234 | 191 | 0.82 |
| `remove_node_attr()`, 500 departures | 10.4 | 4.0 | 0.38 |
| `delete_vertices()`, 500 departures, 50k edges | 2.7 | 0.8 | 0.30 |
| `depart_nodes()`, both of the above | 12.9 | 5.6 | 0.43 |
| 500 arrivals appended across 100 attributes | 12.5 | 4.9 | 0.39 |
| `update_cumulative_edgelist()`, 5% turnover | 7.3 | 4.0 | 0.56 |

Inside the run, Rprof put `depart_nodes()` at 33 ms per step on the old build and 5.6 on the new one; the gap is wider than the microbenchmark because the old `x[-ids]` copies were also triggering garbage collection.

`R CMD check` with the long tests (`NOT_CRAN=true`) passes with Status OK.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a965e27bc706`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.