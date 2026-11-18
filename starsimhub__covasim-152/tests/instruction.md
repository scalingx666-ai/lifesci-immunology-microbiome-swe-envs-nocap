# Issue

**Title:** Automated Docs Workflow

## Description

What this does
---
- Introduces a docs worflow that can be seen working here: https://github.com/jules2689/covasim/actions/runs/80875622
- It is now restricted to run on InstituteforDiseaseModeling/covasim only
- Requires a Deploy Key to push as a personal access token cannot push. Here's how to set that up:
  1. Run `ssh-keygen `(no passphrase)
  2. On https://github.com/InstituteforDiseaseModeling/covasim-docs/settings/keys/new, add the public key here. Make sure to check "write access"
  3. On https://github.com/InstituteforDiseaseModeling/covasim/settings/secrets, add a new secret called `DOCS_DEPLOY_KEY` with the private ssh key

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `571000b2029f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.