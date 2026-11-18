# Issue

**Title:** Sra reads restart redownloads

## Description

There was an issue with metagenomes being re-downloaded on re-run of the metagenomic workflow.
THAT'S NOW FIXED.

Two isssues:
- `import_percent_of_reads_mapped` (and the KrakenUniq import) write into a PROFILE.db after the sample's release flag is written, so every restart found that flag out of date and redid it.
- Each download waits on an earlier sample's release flag, so a redone release forced the next sample's download to run again, which redid that sample's own release, and so on down the whole run.

Fixes:
- The download's gate on an earlier release is `ancient()`, so redoing a release no longer drags a finished download along.
- Releases wait for the files of the steps that `anvi_merge` already waits for (via `get_merge_optional_inputs()`) instead of PROFILE.db, so they are written after the last write into the profile.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bfd43de8f6f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.