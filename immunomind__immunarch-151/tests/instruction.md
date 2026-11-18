# Issue

**Title:** Parsers for new data formats

## Description

- CATT format parser
- RTCR, Imseq and Vidjil formats detection; RTCR parser WIP (existing problem: missing D gene column)
- first working version of RTCR parser
- Imseq format parser
- Vidjil format parser
- added columns for CDR1 and CDR2 to MiXCR parser
- v2_data.Rcmd update

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `778aa4141597`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.