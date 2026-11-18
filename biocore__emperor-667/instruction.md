# Issue

**Title:** BUG: Fix problem with label sizes

## Description

The font sizes would become too small when the text was long and really big when the text was small. I've put in a few scaling factors to make the fonts look good in both cases, and have the "baseline" case be the string `Axis 1 (XX.XX %)`. 

# before bug fix

For long text the font is too small (see the `DaysSinceExperimentStart` label on the first axis).

![bad-size-long-string](https://user-images.githubusercontent.com/375307/39031481-54c2e738-441d-11e8-95c1-b3adb6ad664f.png)

For short text the font is too large (see the `ab` label on the first axis).

![bad-size-small-string](https://user-images.githubusercontent.com/375307/39031487-58eed7f4-441d-11e8-913f-d5a0012e9bc2.png)

# after bug fix

For both cases the font looks *good* now:

![good-size-long-string](https://user-images.githubusercontent.com/375307/39031488-5da94e6e-441d-11e8-8956-a48c1a26cacf.png)

![good-size-small-string](https://user-images.githubusercontent.com/375307/39031494-639349ba-441d-11e8-9d2b-e11dd2b787c5.png)

-----------

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f530eebe6d13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.