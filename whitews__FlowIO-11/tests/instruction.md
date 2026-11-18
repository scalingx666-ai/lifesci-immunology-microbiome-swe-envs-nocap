# Issue

**Title:** Added possibility to read only header and text.

## Description

For me sometimes its very handy to read only the header/metadata of many fcs files, to compare or find out which channels, markers etc. where used, to only read the header information and not the whole data. This saves time and space I suppose, even your FlowIO is very fast anyway. See FlowCores read.FCSheader [https://rdrr.io/bioc/flowCore/man/read.FCSheader.html](url).
I thought that could be handy for others as well and decided to try a pull request.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5860dbabed8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.