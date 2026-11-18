# Issue

**Title:** fix sampling statement for icar_normal

## Description

the call to the icar_normal distribution should be:
`phi ~ icar_normal(N, node1, node2)`, not `icar_normal_lpdf(...`.

back when this model was developed, the Stan compiler allowed this.
for later versions of Stan, this might result in a warning -
I think we're still allowing this as many people made the same mistake -
I naively thought that if you define a function, then you call it by its name.
but a sampling statement is not quite the same thing as a function call -
the Stan compiler maps the distribution name to a corresponding
distribution function, e.g., the sampling statement `y ~ normal(mu, sigma)`
is compiled to a call to the function `normal_lpdf(y | mu, sigma)`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c344ea6dec25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.