# Issue

**Title:** Fast Animation

## Description

I split the Tube rendering into static and dynamic portions.  Static tubes are computed once upon starting playback.  Dynamic tubes are recalculated each frame.  Static tube draw range is recalculated each frame as well.  The effect is that we draw all the animation up to a certain point, then fit a single interpolated segment onto the end of it.  This is much faster than recomputing all the tubes every frame.  

Smooth on 20000 points on my laptop.  Should check it on more hardware since it touches the webGL layer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `027aa16f1dcf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.