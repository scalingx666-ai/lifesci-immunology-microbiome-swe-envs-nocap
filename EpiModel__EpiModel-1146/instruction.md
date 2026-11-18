# Issue

**Title:** simulate_dat(): pass the ergm version to the term initializers

## Description

- Now: ergm's term initializers read the ergm version from disk each time a term is initialized (statnet/ergm#671), and tergm initializes every term of every layer at every time step.
- Goal: avoid those reads until ergm fixes it. About 2 ms per step at 100k nodes and 1 ms of 19 on a 10k model, with the same output.
- How: `simulate_dat()` passes the version through `term.options`, read once per session. It is a workaround, and #1148 tracks taking it out.
- Review: technical, and whether a workaround this small is worth carrying at all.

Part of the run-time work tracked in EpiModel/EpiModelHIV-p#427.

ergm's `InitErgmTerm.*` functions default to `version = packageVersion("ergm")`, which reads the package description from disk every time a term is initialized, and tergm initializes every term of every layer at every time step. That is 25 reads per step in a three-layer EpiModelHIV model, about 0.15 ms each. `simulate_dat()` now passes the same value through `term.options`, read once per session. A version the user sets in `set.control.tergm` is left alone. The output is identical.

The gain is small, and larger in relative terms on small models, where the fixed cost per step dominates. Main (`c665760f`) against this branch, 100 steps, same seed, heap floor raised (`R_VSIZE=1G R_NSIZE=5M`), in milliseconds per step:

| Model | Machine | Full step | `resim_nets` |
|---|---|---|---|
| 100k EpiModelHIV, two tergm layers | Laptop (M5 Max) | 186.3 to 184.1 | 96.8 to 94.7 |
| 100k EpiModelHIV, two tergm layers | Xeon Gold 6526Y | 449 to 448 | 256 to 252 |
| 10k built-in SIS | Laptop | 19.1 to 18.3 | 11.9 to 11.1 |

Laptop figures are means of three replicates, the Xeon ones of two on a shared cluster node, where a difference this size is inside the run-to-run spread.

This is a workaround. The fix belongs in ergm (read the version once when the package loads), and this can come out once that is released.

Accuracy, main against this branch under the same seed: on the 100k model `as.data.frame(sim)` and the complete final run state are identical, and so are eight seeded built-in models (the list is in #1145).

The new `test-ergm-term-version.R` checks that the version is filled in, that a user's `term.options` are kept, and that `simulate_dat()` gives the same network as the call without it. `R CMD check` with the long tests on: 4,981 expectations, no failures. Lint is clean.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9aaebc9eeac8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.