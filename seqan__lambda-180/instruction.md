# Issue

**Title:** update to current SeqAn3 master and add compiler workarounds

## Description

This fixes problems with newer versions of GCC11 and fixes *some* of the problems with GCC10.4, but that last remaining problem I have been unable to fix in the last couple of hours. We will see this on Linux as well as soon as that gets GCC10.4 :|

@SGSSGene do you like weird compiler problems and want to give it a try? 😉 

In any case, I think we can merge these changes (although they are also workarounds at best).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd21ea10b59f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.