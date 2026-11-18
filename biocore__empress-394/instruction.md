# Issue

**Title:** Add "leaf sorting"; reorganize side panel a bit

## Description

- : adds leaf sorting, and changes the default way the tree is drawn to use `descending` leaf sorting (analogous to iTOL's default). It looks pretty nice :)

- : the leaf sorting (and, now, ignore lengths) options are now located in the `Layout` tab of the side panel.

![stuff](https://user-images.githubusercontent.com/4177727/94225447-d124cf00-fea9-11ea-91c6-d721ae4b0cd0.gif)

It is probably worth noting that changing the default to use leaf sorting makes basically all of the README screenshots slightly out-of-date ... it might be worth seeing if we can finagle McHelper to recompute the README screenshots for every commit? (For now I don't think it's a big deal, though.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db2272e28db4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.