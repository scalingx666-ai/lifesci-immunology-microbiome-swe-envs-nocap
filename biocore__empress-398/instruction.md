# Issue

**Title:** Tree statistics

## Description

: adds a "Tree Statistics" tab to the side panel showing the min/max/average node length, as well as node counts (tips, internal nodes, total) for the tree. Also shows node lengths in the selected node menu. (The root node's length is not shown, and is omitted from the node length calculations.) To avoid confusion, renamed "Tree Properties" to "Settings".

Also  (the root node's x1, x2, y1, and y2 in the unrooted layout are all set to 0, regardless of if the root node actually had a length in the input file).

One notable change here is that the BPTree's lengths are now stored as a regular Array, rather than a Float32Array. I noticed that the lengths stored in the application were inaccurate at relatively low precision (e.g. around ~10^-10), and I'd expect normal JS Numbers to have [more precision](https://en.wikipedia.org/wiki/Double-precision_floating-point_format#IEEE_754_double-precision_binary_floating-point_format:_binary64). Switching to use a regular Array seemed to fix the problem.

Another thing worth noting is that now some parts of the UI say "branch length" (e.g. `Ignore branch lengths?` and some say "node length". Not sure which people prefer; can make things consistent if desired.

![stats](https://user-images.githubusercontent.com/4177727/94508873-d0e94400-01c7-11eb-8910-8c3fe46447c5.gif)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dd10852755a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.