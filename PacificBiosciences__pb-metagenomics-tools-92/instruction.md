# Issue

**Title:** updates for v3.3.0

## Description

Upgraded workflows and documentation for snakemake v8:
- Workflows tested with v8.25
- snakemake environment file updated (`snakemake-environment.yaml`)
- Documentation updated for cluster execution modules in snakemake v8

HiFi-MAG-Pipeline:
- sembin upgraded to v2.1, changed command-line syntax
- checkm2 upgraded to v1.0.2
- gtdbtk upgraded to v2.4.0, database must now be release 220, changed command line syntax and metadata gathering
- das_tool upgraded to v1.1.7
- fixed checkm2 database bug in #87 
- fixed issue reported in #86 
- upgraded conda envs may solve #88 
- added memory resources, defaults selected based on benchmarks of typical and deep-sequencing datasets

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18ea90d6ba2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.