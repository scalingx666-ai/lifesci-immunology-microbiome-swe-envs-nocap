# Issue

**Title:** Gate diss_check() on edapprox in netest()

## Description

.

`netest()` gated the `diss_check()` call on `nested.edapprox` alone, which defaults to `TRUE` and applies only when `edapprox = TRUE`. The nesting requirement is a property of the edges dissolution approximation, which subtracts the dissolution correction from the leading formation coefficients in place. A direct STERGM fit estimates formation and persistence jointly and has no such requirement, so a legitimate model was rejected before `tergm()` was ever called. The check now requires `edapprox == TRUE` as well.

On the other question in the issue: the remaining `nested.edapprox` branch in `netest()` is inside the `edapprox == TRUE` arm and is unreachable from the direct path. `update_dissolution()` rejects non-approximation fits outright at the top, so its `diss_check()` call is correctly placed.

One thing worth knowing that came out of the regression test: `tergm` derives its EGMME starting values from the same approximation, so a direct fit whose persistence terms have no formation analog at all still fails, now with tergm's own "No initial parameter method ... Specify via control\$init" rather than ours. That is the correct place for it to fail, and it is fixable by the user with `set.control.tergm = control.tergm(init.method = "zeros")`, which fits the non-nested model in my testing. I added a note to `?netest` covering this.

The test uses a model whose dissolution terms are in the formation model but not as an initial segment (`~edges + nodefactor("race") + nodematch("race")` against `~offset(edges) + offset(nodematch("race"))`). It is rejected under the approximation, term order carries no meaning for a joint fit, and tergm can still initialize it, so the test asserts a real fit rather than just the absence of our error. The truly non-nested case is covered by asserting the error is not ours. `test-netest.R` passes at 165.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5dbba31a58a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.