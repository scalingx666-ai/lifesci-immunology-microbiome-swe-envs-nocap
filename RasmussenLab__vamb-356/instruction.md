# Issue

**Title:** Replace AEMB parser with generic TSV parser

## Description

In issue 355, a user requested to bring back the --jgi option, suc that users can pass in precomputed abundances. That's completely reasonable, and it's not great that the currently recommended way is to use the internal Python types to create an Abundance object.

Instead of bringing back the JGI parser, I made a more generic TSV parser. TSV is a simple, straightforward format also used elsewhere in Vamb. Also, since it's easy to convert the output from --aemb to TSV format, I removed the --aemb option.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c92334765432`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.