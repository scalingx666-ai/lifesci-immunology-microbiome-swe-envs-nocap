# Issue

**Title:** Fix jellyfish detection

## Description

On some versions of bash, `command -v jellyfish` outputs the path to jellyfish to stdout and results in $JELLYFISH_BIN having two paths to `jellyfish` separated by a newline (which obviously breaks the `build_db` script). I've modified it here to redirect the stdout along with the stderr to /dev/null which should fix this edge case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83d33a61e3bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.