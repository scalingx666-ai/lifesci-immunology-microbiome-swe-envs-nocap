# Issue

**Title:** Tag each image with its commit and move master only from the branch head

## Description

The `master` image tag moves with whichever CI run pushes last. A run that finishes after a newer commit's run moves `ghcr.io/ratschlab/metagraph:master` back to its older image. This happened on 2026-11-14: #763's image was pushed at 03:31, and #762's run, for an older commit, replaced it later.

Each pushed image now gets the tag `sha-<full commit>`, so a deployment can pull exactly the commit it means. After the push, the job checks whether the commit is still the head of `master`. Only then it points `master` at the new image with `docker buildx imagetools create`, which takes seconds. `v*` tags are unchanged. Pull requests still build without pushing.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec3969b7044d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.