# Issue

**Title:** Fix a bug with barplot length scaling; abstract and test length-scaling code

## Description

The bug in question occurs when any of the values in the feature metadata field used for length scaling are integer values represented as floats (e.g. `"0.0"`). The mapping between unique numeric feature metadata values and their corresponding lengths is contained in a mapping where, previously, the keys were passed through  `parseFloat()` first. The problem with this is that `parseFloat("0.0")` is `0`, and keys in Objects are treated as Strings -- so the entry for `0` was inaccessible to the nodes with a feature metadata value of `0.0`, bizarrely. (The code [assumes that a value being missing as a key from that mapping means that the value in question was non-numeric](https://github.com/biocore/empress/blob/3d22b50d116fb4317060f2d65f45e91a0cb59029/empress/support_files/js/empress.js#L1360-L1366)... but in this case it was because the Object was created incorrectly.)

Anyway, now the code stores the original string values as the keys in the Object, not the `parseFloat()`-ed values. (This is the same way the color-scaling code works -- the reason that that code doesn't suffer from this bug is likely because I was able to adapt it directly from Emperor, while the length-scaling code required some extra tweaking :) The problematic code in question has also been abstracted to a new utility function, which is now decently tested.

(This bug came up when testing visualizing feature importance scores as barplots -- the majority of importance scores in the `moving-pictures-classifier/feature_importance.qza` file in [this tutorial](https://docs.qiime2.org/2020.6/tutorials/sample-classifier/) are 0s, so I noticed that a lot of these were just missing from the barplot.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3d22b50d116f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.