# Issue

**Title:** Gene highlight in inspect page

## Description

When you search for a gene function in the interactive interface, you can highlight the splits containing genes with a matches. But when you inspect that split, you have to search among the ~20 genes for the one matching your search. ANNOYING.
Solution: highlight the genes:
<img width="1535" height="871" alt="image" src="https://github.com/user-attachments/assets/3fa5ec11-c611-4614-bcd6-f7b371f29aa2" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dee277483ade`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.