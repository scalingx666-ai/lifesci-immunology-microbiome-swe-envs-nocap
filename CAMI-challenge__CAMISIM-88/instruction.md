# Issue

**Title:** Using custom ART error profiles

## Description

Over the last months, we've been using CAMISIM a lot and ended up needing a way to use ART error profiles from our own data with it - I thought this could be something that's interesting for you to have in CAMISIM proper, too.

It works by having the user specify "own" instead of mbarc/hi150/hi/mi as the profile name in the config file, and then there's two additional parameters for the "base name" of the profile files (without "[1/2].txt", like e.g. "HiSeq2500L150R" for the existing hi150 profile) as well as the read length. 
I've added the corresponding parameters to default_config.ini, just for illustration/documentation purposes, but of course it's still compatible with config files that don't have these parameters.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34221ca44479`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.