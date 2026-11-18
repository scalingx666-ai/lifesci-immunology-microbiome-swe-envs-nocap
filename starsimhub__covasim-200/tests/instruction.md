# Issue

**Title:** #192: fixed sidebar height not remaining fixed

## Description

- On sidebar collapse and expand, graphs resize
- Scrolling with sidebar open does not resize the sidebar
- When sidebar grows vertically, scroll page and not sidebar
- Coverted toggle button to vertical bar on sidebar collapse 
- Fixed tooltip making sidebar footer overlap page footer

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93ac923677dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.