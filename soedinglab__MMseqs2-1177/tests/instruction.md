# Issue

**Title:** CI for Nvidia GPU fix

## Description

## Summary

This is a fix for `test-gpu` workflow, which runs on master branch push event.

## What's done

- [x] Setup Github Actions Runner on host with proper GPU & SLURM.
- [x] Fix `test-gpu.yml` to use SLURM for handle jobs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41cb2fabd194`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.