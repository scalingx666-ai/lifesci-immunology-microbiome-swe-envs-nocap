# Issue

**Title:** Add option to create a large screenshot 📸

## Description

Previously we only generated SVG files and PNG files, both of which adopted the resolution of the current window. This PR adds the option to create a **large** resolution version of the plot and save it to a PNG file. This solution was suggested by @rob-knight, who  this as an acceptable alternative to large SVG files.

Currently we scale the resolution to be **5** times bigger, and the prints look great.

Just one open question, should we still print non-high-resolution versions of the plot?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15c9885823d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.