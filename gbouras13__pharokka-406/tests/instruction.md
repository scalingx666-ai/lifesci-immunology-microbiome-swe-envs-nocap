# Issue

**Title:** fix mmseqs fail message

## Description

Super minor change - If MMseqs isn't installed the current version gives an error about foldseek. 

```
try:
        process = sp.Popen(["mmseqs", "version"], stdout=sp.PIPE, stderr=sp.STDOUT)
    except:
        logger.error("Foldseek not found. Please reinstall pharokka.")
```

Update says Mmseqs not found.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9b2e301276a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.