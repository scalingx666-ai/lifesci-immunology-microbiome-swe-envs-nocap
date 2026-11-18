# Issue

**Title:** Closed form estimates / ultrafast fitting when design matrix is categorical

## Description

**This is a work in progress!!! Not ready for review yet!!** It addresses #89 

I have a bare bones implementation of closed form estimates when the design matrix is mutually exclusive categories. Fishes scoring is unnecessary in this case. 

I think a huge number of users a working in this regime*, so let's make it as fast as possible for them. 

Next steps

- [ ] this is currently stand alone code, not integrated into the codebase. I think that `emuFit_micro` should perform a test to see if there simple structure in the covariate matrix. If so, route fitting to `emuFit_micro_discrete`. If not, route to `micro_fisher`. The latter currently happens by default. 
- [ ] currently there it's a reference category constraint. This needs to be general. 
- [ ] Do a million checks that it's doing what we want. I think that data augmentations happen upstream so separating hyperplanes shouldn't be an issue
- [ ] other things that I can't think over right now

*This was very surprising to me, but almost all of the people I've talked to are not doing covariate adjustment. 

I'll keep working on it and request a review from the amazing Dr Teichman when ready.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddcf3e4421a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.