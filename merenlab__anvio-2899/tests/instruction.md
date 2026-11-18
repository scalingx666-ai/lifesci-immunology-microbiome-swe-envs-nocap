# Issue

**Title:** Prettier tables when possible

## Description

This PR (as tiny as it is) addresses a life-long dream of @meren: seeing prettier tables in the terminal output of anvi'o. The difference in code is small BUT IT IS BIG IN THE OUTPUT. The output of this command,

```
anvi-estimate-scg-taxonomy -c CONTIGS.db --metagenome-mode
```

Looks like this before this PR:

<img width="1883" height="583" alt="image" src="https://github.com/user-attachments/assets/1a7e3f09-297b-4a5f-8be8-1176fcf9ee32" />

Looks like this after this PR:

<img width="1879" height="568" alt="image" src="https://github.com/user-attachments/assets/5d3eb177-6e95-45c3-a6f8-91a45a6fa15c" />

Redirection and/or other UTF-8 non-friendly terminals/use-cases go the old way and everything remains in ASCII because @astanin is did an amazing job like that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68092006f68f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.