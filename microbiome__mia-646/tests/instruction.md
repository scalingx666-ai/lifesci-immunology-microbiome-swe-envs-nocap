# Issue

**Title:** Fix splitOn

## Description

introduced an error in splitOn. It is now fixed. This did not work

```
library(mia)
data("peerj13075", package = "mia")
tse <- peerj13075

tse_list <- splitOn(tse, f = "Diet", use.names = TRUE, by = "cols")
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `075697f4e114`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.