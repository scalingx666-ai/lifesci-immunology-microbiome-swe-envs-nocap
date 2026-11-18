# Issue

**Title:** Strobealign aemb

## Description

Thoughts @AroneyS ? Tests pass on my machine, something is wrong with the CI atm. It basically just runs strobealign --aemb, but can output dense or sparse, takes multiple refs and readsets etc, so a little more ergonomic.

Still needs to make a cached strobealign index if there are multiple readsets for a single reference. Also seems like it wouldn't be hard to adjust to `genome` mode too, just by taking a length-weighted average of the means it predicts.

Unfortunately it can't be used as a drop-in replacement for binning, because it only reports mean, not variance.

Once this is through, can copy the template so we can use fairy as well (apparently using it as an API isn't well supported).

ben

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3855fd17699`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.