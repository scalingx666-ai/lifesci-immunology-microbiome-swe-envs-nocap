# Issue

**Title:** simulate_dat(): call ergm::simulate_formula() directly

## Description

- Now: `simulate_dat()` calls `simulate(formula, basis = nw, ...)`. ergm's `simulate.formula()` copies the network, with all of its vertex attributes, twice per layer per time step before it dispatches.
- Goal: avoid the copies. 2 to 15% off the step at 100k nodes, depending on the machine and the heap setting, with the same output.
- How: call `ergm::simulate_formula()` with the same arguments, which reaches the same method.
- Review: technical only. The change is one call; the rest is the test that pins it to the old one.

Closes EpiModel/EpiModelHIV-p#430.

`simulate_dat()` called `simulate(formula, basis = nw, ..., dynamic = TRUE)`. ergm's `simulate.formula()` attaches the basis network to the formula and evaluates the formula again before it dispatches to `simulate_formula()`, and that copies the network with all of its vertex attributes twice per layer per time step. This PR calls `ergm::simulate_formula()` with the same arguments, which reaches the same method without the copies. The output is identical.

The gain grows with the number of nodal attributes and with how slow the machine's memory is. On a 100k-node EpiModelHIV model (three layers, 81 nodal attributes, restarted from a calibrated run), 100 steps, same seed, main (`c665760f`) against this branch, in milliseconds per step:

| How it ran | Heap | Laptop (M5 Max) | M1 Max | Xeon Gold 6242 | Xeon Gold 6526Y |
|---|---|---|---|---|---|
| One process | default | 314 to 293 | 516 to 476 | 1183 to 1048 | 846 to 808 |
| One process | raised floor | 258 to 254 | 451 to 428 | 902 to 836 | 634 to 586 |
| 8 forked simulations | default | | | 1287 to 1111 | 1004 to 850 |
| 8 forked simulations | raised floor | | | 953 to 878 | 674 to 626 |

"Raised floor" is `R_VSIZE=1G R_NSIZE=5M`, which removes most of the garbage collection these copies were causing; the rest is the copying itself. Laptop and M1 figures are means of three replicates, the Xeon ones are one run per arm on a cluster node. A 10k-node built-in SIS model does not change (18.6 ms per step on both builds).

Accuracy, main against this branch under the same seed:

- On the 100k model, `as.data.frame(sim)` and the complete final run state (attributes, edgelists, cumulative edgelists) are identical on all four machines.
- Seven seeded built-in models are identical, including `get_nwstats()`, the transmission matrix and, for full networks, the edge spells: a full network simulated once, a full network resimulated every step with vital dynamics, tergmLite with network statistics and the cumulative edgelist, a one-step layer, two layers, duration tracking with `mean.age`, and two simulations in one call.

The new `test-simulate-dat.R` pins `simulate_dat()` to the old `simulate()` call under the same seed on a tergmLite network, a `networkDynamic` and a one-step layer. Full suite: 4,976 expectations and no failures, against 4,967 on main. Lint is clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab466fafa7ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.