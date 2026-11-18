# Issue

**Title:** CI: remove action to install ipfs, update pixi

## Description

The [public gateway](https://blog.ipfs.tech/2026-08-beyond-sponsored-gateways/) is going away, and none of the `setup-ipfs` account for that. So probably it is better to just remove it?

Also update pixi to `0.81.0`, bumping the lock file to v7.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cfb6dbaaeab8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.