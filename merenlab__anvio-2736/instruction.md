# Issue

**Title:** Workflow fixies

## Description

Couple of small issues, one PR to fix them.

- Autowire max_thread with --resources nodes=<max threads>. And updated the documentation around that.

- Added back the max_thread option in the workflow's config file. It was still usable, but present in default config files. I missed that during the refactor.

- Some log output directories were not created before a job would run. Clusterize is *really* not happy if there is no directory for its job's log. @ivagljiva fixed most of them here #2732, I added more jobs on that list.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `25bd42778efa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.