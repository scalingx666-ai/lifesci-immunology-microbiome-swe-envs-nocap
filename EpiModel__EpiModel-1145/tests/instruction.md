# Issue

**Title:** simulate_dat(): read the tergmLite edgelist from the sampler's state

## Description

- Now: in a tergmLite layer `simulate_dat()` asks tergm for the final network. tergm builds it as a networkLite, and `set_network()` turns it straight back into an edgelist.
- Goal: skip that round trip. About 10 ms of a 186 ms step at 100k nodes, with the same output.
- How: ask tergm for the sampler's state and read the edgelist from it. A layer that tracks durations keeps the old route.
- Review: technical only. This is run-time work and nothing about the model changes.

Part of the run-time work tracked in EpiModel/EpiModelHIV-p#427.

In a tergmLite layer `simulate_dat()` asked tergm for `output = "final"`. tergm then turns the sampler's state into a networkLite (`add.edges()` on tibbles: `bind_rows()`, `order()`, `duplicated()`), and `set_network()` turns the networkLite straight back into an edgelist. This PR asks for `output = "ergm_state"` and builds the same edgelist from the state. A layer with `tergmLite.track.duration = TRUE` keeps the old route, since it needs the network attributes of the final network. The output is identical.

Main (`c665760f`) against this branch, 100 steps, same seed, heap floor raised (`R_VSIZE=1G R_NSIZE=5M`), in milliseconds per step:

| Model | Machine | Full step | `resim_nets` |
|---|---|---|---|
| 100k EpiModelHIV, two tergm layers | Laptop (M5 Max) | 186 to 175 | 97 to 86 |
| 100k EpiModelHIV, two tergm layers | Xeon Gold 6526Y | 449 to 435 | 256 to 242 |
| 10k built-in SIS | Laptop | 19.1 to 18.0 | 11.9 to 10.9 |

Laptop figures are means of three replicates, the Xeon ones of two on a shared cluster node. With #1144, #1146 and #1147 as well, the Xeon step goes from 449 to 376.

Accuracy, main against this branch under the same seed:

- On the 100k model, `as.data.frame(sim)` and the complete final run state are identical on the laptop, and `as.data.frame(sim)` is identical on the cluster.
- Eight seeded built-in models are identical, including `get_nwstats()`, the transmission matrix and, for full networks, the edge spells: a full network simulated once, a full network resimulated every step with vital dynamics, tergmLite with network statistics and the cumulative edgelist, a one-step layer, two layers, duration tracking with `mean.age`, two simulations in one call, and two groups.

The new `test-simulate-dat-edgelist.R` pins `simulate_dat()` to the `output = "final"` route under the same seed, on a persistent layer, a one-step layer and a layer that tracks durations. `R CMD check` with the long tests on: 4,989 expectations, no failures. Lint is clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c665760f4194`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.