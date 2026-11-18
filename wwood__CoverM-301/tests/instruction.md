# Issue

**Title:** Update finch to 0.6.3 and needletail to 0.7

## Description

finch 0.6.3 requires needletail ^0.7, and needletail carries a
`links = "lzma"` native library, so only one needletail major version
can exist in the dependency tree. Move coverm's direct needletail
dependency from 0.5.* to 0.7.* to match.

galah is the other consumer of finch/needletail in the tree. Its
published 0.5.2 still pins needletail 0.5.*, which is incompatible with
needletail 0.7, so depend on galah from git (main already uses
needletail 0.7 and finch 0.6.*) until a galah release with needletail
0.7 is published.

Claude-Session: https://claude.ai/code/session_01RgeCVEEvbQV5aZR6yST5FU

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2714a8e01b57`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.