# Issue

**Title:** ENH: Enlarge selected samples in Emperor

## Description

. Ideally we'd have options for choosing how to visually represent selected samples, but I think enlarging is a more robust solution than the emissive stuff.

Emissives are still used for representing samples selected in Emperor using the dragging options -- the scaling stuff is only used for representing samples that contain a given selected node/nodes in Empress. I think having these things be split up looks nice, personally.

There are still the Emperor scale controls available, which would mess with things here (allowing for all sorts of interaction bugs -- e.g. the user re-scales the samples or something in Emperor only for that re-scaling to get lost when the user selects/unselects nodes in Empress), but honestly we could just hide that part of the Emperor menu and I think that'd be good enough for now...?

![fancy](https://user-images.githubusercontent.com/4177727/95253755-b6205c00-07d3-11eb-9a68-d3fd42f013a9.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b53a17da8da3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.