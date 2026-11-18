# Issue

**Title:** Fix input check

## Description

Hello!

I noticed that this input check fails if there are missing values. It leads to ambiguous error:
```

library(decontam)
st <- readRDS(system.file("extdata", "st.rds", package="decontam"))
conc <- c(6413, 3581.0, 5375, 4107, 4291, 4260, 4171, 2765, 33, NA)
isContaminant(st, conc=conc)
```

> Error in if (!(is.numeric(conc) && all(conc > 0))) stop("conc must be positive numeric.") : 
>   missing value where TRUE/FALSE needed

-Tuomas

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4137e5769d27`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.