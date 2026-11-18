# Issue

**Title:** Add module for outputting Kraken-style taxonomy report and --taxLineage

## Description

- adds module taxonomyreport for Kraken-style taxonomy report
- add parameter --taxLineage to par.lca for lca, taxonomy and addtaxonomy. Currently this means there is a variable number of fields in the output, which isn't optimal
- refactored NcbiTaxonomy:
  - does not load delnodes.dmp anymore. When a taxon that was seen in a report is not in the taxDB, it could be either through 
  - get rid of two maps; instead D is vector mapping TaxID to internal ID
  - use TaxID type to better distinguish interal IDs and taxIDs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c554b3b41502`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.