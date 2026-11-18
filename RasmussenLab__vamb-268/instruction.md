# Issue

**Title:** Output .tsv files in actual TSV format

## Description

It turns out TSV has an actual specification, see
https://www.iana.org/assignments/media-types/text/tab-separated-values and https://www.loc.gov/preservation/digital/formats/fdd/fdd000533.shtml#notes However, Vamb did not follow this specification, as the header line was missing. This is problematic, because external TSV parsers may not correctly parse the output files. It's also just annoying for users.

In this commit, add a header line to all output .TSV files. This is a breaking change, so let's get it in before v5.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7edd6201bec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.