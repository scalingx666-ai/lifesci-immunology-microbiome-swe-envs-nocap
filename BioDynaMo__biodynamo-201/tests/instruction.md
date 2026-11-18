# Issue

**Title:** Avoid overriding results

## Description

Currently, BioDynaMo overrides previous results even if `remove_output_dir_contents` is set to `false`. This is problematic since the simulations can be computationally expensive and you don't want to override them by default. With this PR, we introduce subfolders to the existing output folder structure or the type "YYYY-MM-DD-HH:MM:SS".

For instance, running the `soma_clustering` demo five times results in the following folder structure:
```
~/Programming/biodynamo_projects/soma_clustering on  master! ⌚ 15:21:50
$ tree output 
output
└── soma_clustering
    ├── 2021-08-10-15:21:43
    ├── 2021-08-10-15:21:45
    ├── 2021-08-10-15:21:46
    ├── 2021-08-10-15:21:48
    └── 2021-08-10-15:21:49

6 directories, 0 files
```
I also added tests verifying this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a56fd81699e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.