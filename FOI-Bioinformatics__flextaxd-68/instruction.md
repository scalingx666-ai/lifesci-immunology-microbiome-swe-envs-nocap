# Issue

**Title:** various fixes

## Description

- Added automated genome through NCBI "datasets" software. This occurs only on user-prompt and no previous download methods or calls have been changed.
- Made minor additions to input argument parser, allowing more consistent input (e.g., previously some arguments stated "database" and others "db". Now made shortened "db" versions across input args.)
- Added input type "GTDB", which will remap to QIIME. This did not feel intuitive for a new user that creates a GTDB database and had to specify --taxonomy_type QIIME. (Is QIIME the standard format for GTDB?)
- In tree plotting:
  - Added functionality to force full node label length writeoute
  - Added user-control of label size
  - Removed top and right borders, it prevents labels from being outside the plot borders
 - FATAL: Fixed import of genomeid2taxid parsing (ReadTaxonomy.py), where the first line was parsed as a header (not specified for genomeid2taxid 
 file) and thus ignored the first genome. This does not apply for the NCBI accession2taxid parser (the NCBI accession2taxid file has a header), occuring in ReadTaxonomy_NCBI.py)
- Removed debugging message that previously attempted to iterate over an integer. To be further implemented, if needed.
- Drafted a genome-file matching function based on regular expression. Not used at the moment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79e2404812d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.