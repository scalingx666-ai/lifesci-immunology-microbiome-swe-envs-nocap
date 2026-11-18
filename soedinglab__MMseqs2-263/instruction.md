# Issue

**Title:** Clarify parameter help in `mmseqs view`

## Description

I was a little confused by the way the description for `--idx-entry-type` was written. I think this makes it clearer.

I'm actually not quite sure what the difference between `sequence` vs `src sequence` and `header` vs `src header`. Though I haven't looked closely at the docs either, so that's probably on me...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f644744a81f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.