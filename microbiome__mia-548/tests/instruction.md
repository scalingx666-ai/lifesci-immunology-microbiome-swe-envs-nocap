# Issue

**Title:** Tree agglomeration fix

## Description

I noticed that tree agglomeration was not done correctly.

The previous method used `drop.tip()` with `drop.internal` option. This was problematic because of the following reason.

- Nodes of rowTree represents rows. A row can be in internal node, it does not have to be in tip. Sometimes internal node does not belong to any other row (for instance child node of this kind of internal node could represent other row).
- When `drop.internal` option is used, the whole branch corresponding to the tip being removed is dropped. It can be that we lose internal node representing specific row, if the internal node does not have any child nodes that are kept.

Now the pruning is done one tip-layer at the time to ensure that we keep all nodes that represent rows.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1926161c86b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.