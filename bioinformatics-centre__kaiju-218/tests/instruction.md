# Issue

**Title:** Makedb for Mar Databases

## Description

Howdy, @pmenzel 

Here's the final update as promised. A short summary of what has been done:
- MakeDB now queries our API for metadata and outputs versioning + some general statistics along the way
- Download stage prioritizes NCBI sequence data. Where this is missing, locally predicted Prokka CDS are used instead, and this happens seamlessly based on available db-versions. Also, massive speed-up.
- mar_mags has been removed. Discrete db divisions available are mar, mar_ref and mar_db
- jq added as a dependency for json parsing. (standard in most distributions, or trivial installation via apt/yum)
- Colorized output to easily distinguish between build stage info (echos in script) and general stdout from tools/scripts using terminal color codes. If this breaks any sort of compliance or you just hate colors, i will remove it :)

Merging closes issues #193 #194 and #179

Have a nice weekend!
-Espen

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1251f3915cfa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.