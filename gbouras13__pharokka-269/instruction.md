# Issue

**Title:** Allow for non standard translation table

## Description

Fixed issue with gff/gbk generation defaulting to translation table 11 regardless of what argument was passed into pharokka.

Primarily through adding 'table = coding_table' to the Biopython translate function (without which it defaults to 11)

Output using translation table 4 in current version
![image](https://github.com/gbouras13/pharokka/assets/19933700/6cce542e-281a-42d5-9843-92bf4da32bf7)

Output using translation table 4 in pull request version
![image](https://github.com/gbouras13/pharokka/assets/19933700/1edbc3bb-e24a-424b-95c7-f20314a93b35)

note apologies for the multiple commits, was literally editing within github on the fly, which seemed to require a commit every time I wanted to open a different page/script

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b8b487451f8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.