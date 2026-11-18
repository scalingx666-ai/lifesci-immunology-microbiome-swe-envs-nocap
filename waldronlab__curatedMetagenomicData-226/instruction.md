# Issue

**Title:** Add filterByDataType

## Description

This is my initial pass. I would appreciate feedback to improve as I'm still learning R, Bioconductor, etc., and may not be familiar with conventions or the best way to do things.

I selected the second suggested function style--was the first way the more "R way" to approach the problem?. I wrote some documentation but I wanted to ask what would be better examples and test cases? I haven't tested a large dataset as the function sometimes kills my R session and I'm not sure yet if this is my bad programming or not enough memory.

One thing I noticed is that when I did the `selectWhere("relative_abundance", age >= 30, age <= 40, smoker == "yes")`, I noticed that I got NAs  for age in the result despite specifying that age should be >=30 and <= 40. Is this behavior expected?

Thanks for your feedback.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5f08acf027a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.