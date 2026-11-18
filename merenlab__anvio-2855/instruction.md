# Issue

**Title:** Hide npm audit fix --force

## Description

Running `npm audit fix --force` in `anvio/data/interactive` upgrades jQuery to 4.x, which Bootstrap 4 refuses to run with, so the interfaces hang on loading screen.

The solution: hide the message from npm about the audit fix --force, of course :)

<img width="820" height="661" alt="image" src="https://github.com/user-attachments/assets/487c7b52-56ec-45f1-ae0a-bcfce18ab7e8" />

Also: `is_all_npm_packages_installed()` now catches a package.json that npm rewrote or installed packages whose versions differ from their pins. It explains that the audit warnings don't apply to a locally running interface, and prints the commands to restore the pinned versions.

A follow up PR would be to upgrade jQuery version to 3.7.x. That requires more testing to make sure the interface is not dead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65149bd29780`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.