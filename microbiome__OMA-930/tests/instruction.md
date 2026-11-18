# Issue

**Title:** Add reader orientation sections to the landing page

## Description

Adds short reader-orientation sections to the landing page (`index.qmd`), following other Bioconductor books: [OSCA](https://bioconductor.org/books/release/OSCA/) ("What you will learn", "What you won't learn", "Who we wrote this for") and [csawBook](https://bioconductor.org/books/release/csawBook/) / [SingleRBook](https://bioconductor.org/books/release/SingleRBook/) ("How to get help").

New sections, placed before "Building OMA book":

- **Who this book is for**: refers to the Training and Resources chapters for introductory material.
- **What you will learn**: data containers, common analysis steps, reproducible workflows.
- **What you will not learn**: raw read processing (refers to Import) and general R/statistics introductions (refers to Training and Resources).
- **How to get help**: refers to the Support chapter and GitHub issues.

The sections are kept short and point to the existing chapters for details.

Rendered `index.qmd`; all cross-references resolve.

Note: PR #918 also edits `index.qmd` (Welcome heading, cover image, version line). The new sections are added in a part of the page that #918 does not change, so the two PRs should merge without conflicts.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afa1a428a8d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.