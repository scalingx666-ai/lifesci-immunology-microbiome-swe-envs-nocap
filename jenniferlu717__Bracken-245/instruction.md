# Issue

**Title:** Reduce memory overhead and exit early if not able to create database.…

## Description

This PR seeks to address two issues:

### 1. Reduce memory overhead during the creation of `database.kraken` 
It seeks to avoid any *potential* memory overhead incurred by having the `find` command concatenate the FASTAs  and input that data to  the `classifier` via process substitution.

### 2. Exit early if failed to build `database.kraken` 
The change-set alters the behavior of the build script to finalize the name of the database only if the build process has successfully completed. This avoids potential false positives when running `bracken-build` in a loop as demonstrated below:

```
for i in {50,75,100}; do
    bracken-build -d . -t 12 -l $i
done
```

Currently, if `bracken-build` fails for read length `50` the loop will still continue since `database.kraken` exists regardless of whether the previous invocation succeeded or not. This will have the cascading effect of read length 75 and 100 being processed on a potentially truncated database.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `835c65b45acb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.