# Issue

**Title:** Add option to adjust gap between tree and first barplot layer

## Description

Adds a new element to the side panel that allows users to manually set the distance between the tree and the first barplot layer. Currently works by specifying a percentage increase to `_maxDisplacement`. ~Default value is 10 (1 + 10% = 1.1) to keep with current default behavior.~ Default value changed to 5 as we decided to decrease the default gap.

OLD: `var maxD = 1.1 * this._maxDisplacement;`

NEW: `var maxD = (1 + this._displacementFrac) * this._maxDisplacement;`

~A new function `Empress.prototype.changeBorderGap` just divides the input value by 100. This can likely be rewritten to not use a whole function - depends on what people think looks more clean.~

## Current Status

- [x] Pick a better display name than `Separation length`
- [x] Update relevant documentation in `empress.js`
- [x] Disallow negative values

![gap_movie](https://user-images.githubusercontent.com/4030868/101989613-241b5080-3c67-11eb-9c81-419d4adef16e.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b7a8d3a8da2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.