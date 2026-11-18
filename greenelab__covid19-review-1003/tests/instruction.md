# Issue

**Title:** Cache pharmaceuticals references on 2021-08-13

## Description

I quickly reviewed all the references in the pharmaceuticals manuscript and corrected errors in #993.  Now that these references are in a fairly clean state, I'm caching them to a file.  This should help speed up builds (only slightly, because it only adds ~100 new references).

To generate this list I commented out this part of `build.sh`
```
rm -rf output/$INDIVIDUAL_KEYWORD
```
and used
```
BUILD_PDF=false BUILD_HTML=false BUILD_INDIVIDUAL=true build/build.sh
```
locally to get the `references.json` output file for the pharmaceuticals manuscript.  Then, I removed entries that were already in `manual-references.bib` or `manual-references.json` and renamed the JSON file.  This has duplicates of many references from `manual-references-2021-02-08.json` but I left them in.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc4742ee10ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.