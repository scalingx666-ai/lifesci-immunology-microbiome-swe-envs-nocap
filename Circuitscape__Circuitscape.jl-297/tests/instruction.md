# Issue

**Title:** Reduce error tolerance for matrix norms when using single precision

## Description

I had to increase the tolerance of error for the matrix norm testing to `1e-3` when using single precision. The tolerance is `1e-5` when using double. I have confirmed that this stops the `AssertError` from being thrown in the Omniscape test that was failing (and did not fail when I changed the test parameter to use double precision). 

If it is any consolation, regardless of the error in the matrix norm, using `Float32` yields pretty much the exact current map as using `Float64` ([these tests](https://github.com/Circuitscape/Omniscape.jl/blob/main/test/runtests.jl#L121-L123) pass in Omniscape regardless of the precision used -- a good sign).

This may be related to #288, but we have not confirmed with the user whether single precision is being used there. I suspect it is, but we will verify before closing that issue.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5a79911e1ea5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.