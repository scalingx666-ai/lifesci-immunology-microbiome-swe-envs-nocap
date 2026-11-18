# Issue

**Title:** BUG: Draw node circles as needed in SVG export

## Description

Noticed that node circles were being left out of the SVG tree export, even when node circles are explicitly enabled for some or all nodes.

I believe this was happening because `export-util.js` hadn't been updated in light of #486's changes:

https://github.com/biocore/empress/blob/df3a4da5a5b23d465937112dfa2050f8957bb0ed/empress/support_files/js/export-util.js#L337

The `Drawer.showTreeNodes` flag was removed in #486, so I guess thanks to Javascript's magic `if (drawer.showTreeNodes)` will always silently evaluate to `undefined` (aka false) ._.

This PR fixes this problem. Fortunately, the way #486 is set up seemed to make it pretty easy to get this working again.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df3a4da5a5b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.