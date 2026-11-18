# Issue

**Title:** Add metadata to biom table

## Description

## Problem
While working with the output BIOMs form this great tool I found out that not all tools like it when a BIOM file has no metadata. 

## fix
To fix this problem I've added the option for the user to add tsv metadata file to the BIOM file. These files can be [Qiime](http://qiime.org/documentation/file_formats.html#mapping-file-overview) style mapping files.

With `-m` you can tell which metadata file should be added. The first column in the metadata file needs to be the sample names (same as the imported files). 
When no metadata file is given as input dummy metadata is made. This is the sample name.
`{"Id": sample name}`  This way there is always metadata in the BIOM file. 

## changes made

- Added `-m/--metadata` to argparser
- Unittest for dummy metadata
- Import pandas for reading tsv file
- Add dummy metadata if none is added
- bumped version number to 1.1.1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46b32df9b3eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.