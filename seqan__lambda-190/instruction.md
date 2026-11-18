# Issue

**Title:** [fix] view madness in seqan2

## Description

---

SeqAn2 deep internally expects things to be default-constructible which some of our view are no longer. It is also no longer possible to workaround this... but it is possible to specialise lots of stuff within in SeqAn2 to not trigger any default-initialisations which is super-unsafe... but works ™️ 

---

SeqAn2 is both 💩 and 🎉 because while the craziness is infinite, you can always work around it, by adding more 💩

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3810affe28a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.