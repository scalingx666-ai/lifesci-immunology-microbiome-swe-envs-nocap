# Issue

**Title:** Fixes problem with the camera not being centered

## Description

The problem was that the camera assumed all coordinate spaces were centered around the origin. This assumption is not always true and it is **almost always** not true for weighted UniFrac (hence the panning of the camera in the screenshot in #696). While fixing this, I noticed that the target of the camera had an offset making plots rotate in an awkward way, this was fixed by adding calculating the target.

I also noticed that "re-centering" wasn't working properly either, re-centering the camera would lead to "almost" centered scenes. This last problem was fixed by disabling inertia/damping in the scene's controls.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62e87f48d97a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.