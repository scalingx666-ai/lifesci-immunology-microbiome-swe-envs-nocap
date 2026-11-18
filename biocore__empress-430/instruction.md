# Issue

**Title:** Fix circular layout scaling bug and add regression tests; remove startAngle circular layout parameter

## Description

and adds tests to verify it'll remain addressed. We may want to eventually try to remove the scaling stuff entirely (?), but for now at least it shouldn't break "linear" trees in the circular layout any more.

I also removed the (unused) `startAngle` parameter of the circular layout function. Theoretically, it would have been possible for the caller to specify `startAngle = Math.PI / 2`, which would mean that all of a sudden the #429 problem would become that the circular layout tree is a straight _vertical_ rather than a horizontal line -- but when we implement rotation (#359), as I understand it, it'll happen much later on down the line (after computing layout stuff), so no need to make our job harder.

The other main change here (as part of #429) is that I abstracted the scaling factor code from the circular and unrooted layouts into its own function, `computeScaleFactor()`. The circular and unrooted layouts handled this slightly differently before -- both would compute `widthScale` and `heightScale`, but circular would use the max of these for scaling while unrooted would use the min. For consistency's sake, both now use the max (this is why the existing unrooted layout test's values were changed).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `26f1b02caa00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.