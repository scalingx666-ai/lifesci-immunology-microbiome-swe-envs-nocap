# Issue

**Title:** add a download-db cli command

## Description

This PR provides a new command `charcoal download-db`, which
downloads the GTDB sbt.zip and lineages CSV in `db/` using snakemake. This also adjusts the default system config to have those paths.

Note that we cannot use the default Snakefile as with the rest of the commands because the default Snakefile does all sorts of configuration checking, which won't succeed when the databases aren't there. That having been said I really like using snakemake to download files... we could use it with sourmash!

This PR addresses #61 but doesn't solve it - ultimately we want to allow the database to go to a project-independent location - but this will suffice for a release, I think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44d393727914`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.