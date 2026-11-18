# Issue

**Title:** Restructure `ROOT` support based on `Xcode` version

## Description

ROOT, especially cling, reacts very sensitively to Xcode updates. The last Xcode update to 14.1 broke the previous Root build (6.25.01) on macOS. With this PR, we no longer version our ROOT builds with macOS version but rather with the XCode version allowing better backward compatibility.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46996fef099d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.