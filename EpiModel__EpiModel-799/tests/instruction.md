# Issue

**Title:** low level logic to disable modules

## Description

WIP

- makes a named list of module on initialization
- add a "utility module" afeter `updater_net` that will disable modules listed in `param$.modules.to.disable`
- this param is cleared after the modules are disabled
- meant to be used with scenarios to chose at what time to remove what modules

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7aa3a975f936`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.