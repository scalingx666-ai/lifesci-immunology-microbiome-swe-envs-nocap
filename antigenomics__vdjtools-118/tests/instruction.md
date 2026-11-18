# Issue

**Title:** Adding /usr/share/java to gradle repo path

## Description

Hello,

Debian places .jar files in the directory "/usr/share/java". This patch supports gradle to find these.
All build dependencies are already shipping with Debian.
I apologize for the extra diff on the missing final newline that github's editor auto-added.

Cheers,

Steffen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `03ec87e3e39c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.