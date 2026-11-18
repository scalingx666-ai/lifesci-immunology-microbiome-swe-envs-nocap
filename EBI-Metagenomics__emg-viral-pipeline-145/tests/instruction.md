# Issue

**Title:** Fix sankey plots

## Description

Resolving issue 
- krona plots had reversed taxonomy and plots were incorrect. I also added `undefined_rank` to be aligned with sankey plots
<img width="914" alt="image" src="https://github.com/user-attachments/assets/b31ff663-c56d-4b07-9464-4c84d979f154" />
- sankey (made undefined_taxa blank because it overload a plot)
<img width="1468" alt="image" src="https://github.com/user-attachments/assets/8ee89e77-8e92-4b42-8907-4ce337684fa3" />

Note: failing test would be fixed after PR  because it is related issue

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `081e6ed0273f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.