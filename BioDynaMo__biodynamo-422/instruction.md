# Issue

**Title:** Add Ubuntu 24.04 support

## Description

# Add Ubuntu 24.04 Support

## Changes Made

- **Ubuntu 24.04 Support**: Added installation files and package lists for Ubuntu 24.04
- **OpenMP Fix**: Fixed OpenMP header detection for newer GCC versions
- **Valgrind Update**: Added memory leak suppressions for Ubuntu 24.04 
- **CI Updates**: Updated GitHub Actions to test on Ubuntu 24.04

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05e3a328bfee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.