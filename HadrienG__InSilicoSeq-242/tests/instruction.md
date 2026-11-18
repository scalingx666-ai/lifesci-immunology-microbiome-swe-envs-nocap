# Issue

**Title:** Additional Amplicon sequencing features

## Description

Hi!

I put together a few more commits related to the amplicon sequencing mode. 
The new feature is an input file that uses simple read counts and disables the abundance calculation altogether. We didn't need the abundance or coverage calculation, our preprocessing tool gives us the exact read count we want to simulate for every amplicon/genome. 

Additionally, I have a few more things I would like to ask your input on:
1. The multithreading during read generation currently only works by splitting up the load for every single reference genome/amplicon. In our amplicon simulation we often have many amplicons with few reads each, so the load splitting is not efficient. A method of batching multiple amplicons to each worker would be better, but this would require a lot of rewriting of the main `generate_reads()` function, which is already very long. Would you mind if I send a PR with a rewrite of that function?
2. There looks to be some consistent code styling in here, but I do not see any mention of them, other than pycodestyle in the requirements. I have been very happy with the tools `black`, `isort`, and `flake8`, and setting them up using a pyproject.toml. We could also add the styling checks in the github action runner. Do you have a preference on this?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e75b2a7ee9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.