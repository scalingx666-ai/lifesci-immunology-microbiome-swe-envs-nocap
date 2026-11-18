# Issue

**Title:** Add `--min-num-reads` parameter for discov

## Description

This PR adds another flag to the discov-computing programs `anvi-profile-blitz` and `anvi-summarize`. One issue I noticed with the discov calculation was that very few reads mapping to a reference could get very high discov scores. If just a handful of reads map, we don't expect many windows of the reference to be covered and hence normalized spread (num covered windows / num expected windows) could be very high. And similarly, if each read maps in isolation, the mean coverage depth in those covered windows would all be quite similar and therefore evenness could be high as well. The problem is that with so few reads mapping, it is difficult to distinguish true randomness (what we are looking for as evidence of presence) from noise.

So this PR gets around this problem by setting a minimum requirement for the number of reads mapping to a sequence (`--min-num-reads`). If the number of mapped reads is below this number, we still compute spread, but we artificially set normalized spread and evenness both to 0. In which case, the spread-evenness score C = 0 and therefore discov collapses to detection squared (which will likely be very small with so few reads mapping, unless the reference itself is extremely short).

I haven't extensively tested this yet, so the current default of 10 reads was set based on a handful of observations (I kept seeing the high discov/few reads issue with number of reads < ~6). I want to test it a bit more before merging.

This is a  and should be merged after that PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `071e72fad3c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.