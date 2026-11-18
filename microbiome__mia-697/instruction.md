# Issue

**Title:** C++ implementation of the Stacked Faith algorithm

## Description

This PR implements a fast C++ algorithm (via Rcpp) for calculating Faith's index, based on the C++ code from the sources in #522. For simplicity, I ended up extracting the Faith-related code and condensing it into just a few source files, and doing some amount of rewriting to simplify the code and integrate it more smoothly with R.

The algorithm can be toggled with the parameter `fast.faith` to `addAlpha()` (`TRUE` by default). Based on my own testing, even large datasets have their indices calculated pretty much instantly.

```
> tse <- microbiomeDataSets::GrieneisenTSData()
> system.time(x <- addAlpha(tse, index="faith", fast.faith=TRUE))
   user  system elapsed 
   0.47    0.03    0.50 
> system.time(x2 <- addAlpha(tse, index="faith", fast.faith=FALSE))
   user  system elapsed 
  35.93    0.47   36.92 
> sum(abs(colData(x)$faith - colData(x2)$faith) > 0.00000001)
[1] 7
```

As you can see in the example, the output of the new algorithm may sometimes differ somewhat from the old one. This is because the new algorithm always includes lengths all the way down to the root in its calculations, while the old algorithm seems to drop them sometimes during the process of pruning the tree. In concrete terms, the new algoritm matches the output of `picante::pd()` with `include.root=TRUE`, while the old algorithm matches `include.root=FALSE`. For most datasets I checked this did not lead to significant differences, but for e.g. `SprockettTHData` from `microbiomeDataSets` there is a consistent difference of ~1.17 for basically every sample. I don't know how significant this is going to be in practice, however.

Another thing to note is that the original C++ code is licensed under the 3-clause BSD license - this is compatible with mia's licensing, but I'm not sure what, if anything, needs to be done to properly indicate this in the package.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `198360cb5e3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.