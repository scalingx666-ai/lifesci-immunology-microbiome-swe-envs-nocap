# Issue

**Title:** Position the selection menu normally, even for nodes with duplicate names (when clicked on)

## Description

. (More specifically, this addresses the second and currently-only-unchecked point in #169.)

When a node is clicked on, `CanvasEvents` already finds its key (an umambiguous identifier) in `empress._treeData`. Now, this key is used to center the camera on the node that was clicked on, as well as only highlight this node in green. Additionally, I believe the sample presence info should now be correct (since no iteration is done over all of the nodes with this name).

If a node is selected by searching and its name is ambiguous, then the old behavior is used (the camera is centered on the root, and all nodes with this name are highlighted). However, now there's some extra work done in the selection menu code that hides the sample presence info for this case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21c2773c9a3f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.