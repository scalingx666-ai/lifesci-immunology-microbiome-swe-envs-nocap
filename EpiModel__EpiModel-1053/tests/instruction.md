# Issue

**Title:** Add Correct ylabs to netdx #1051

## Description

Add y-axis label for netdx duration and dissolution plots. 
Also forward the axis arguments to the boxplot method

```r
    num <- 50
    nw <- network_initialize(n = num)
    formation <- ~edges
    target.stats <- 15
    coef.diss <- dissolution_coefs(dissolution = ~offset(edges), duration = 20)
    est1 <- netest(nw, formation, target.stats, coef.diss, verbose = FALSE)
    dx1 <- netdx(est1, nsims = 1, nsteps = 10, verbose = FALSE)
    
    par(mfrow = c(2, 2))
    plot(dx1, type = "duration", mean.smooth = FALSE)
    plot(dx1, method = "b", type = "duration")
    plot(dx1, type = "dissolution")
    plot(dx1, method = "b", type = "dissolution")
```


<img width="1200" height="990" alt="image" src="https://github.com/user-attachments/assets/1b66c6f0-1e4c-4687-aa1c-b9076ec1a804" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70317a7d90bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.