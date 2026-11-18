# Issue

**Title:** jessika-fuessel from contributors to devs file

## Description

The CI is failing on anvio.org with message:

```
Traceback (most recent call last):
  File "/home/runner/work/anvio.org/anvio.org/_scripts/update-programs-info.py", line 20, in <module>
    p.init_programs()
  File "/home/runner/work/anvio.org/anvio.org/anvio_source/anvio/programs.py", line 397, in init_programs
    raise ConfigError(f"The following programs have authors who are not defined in the authors YAML file "
anvio.errors.ConfigError: 

Config Error: The following programs have authors who are not defined in the authors YAML file
              (jessika-fuessel) -- every author listed in anvi'o programs must have an entry  
              in the authors YAML file: anvi-gen-function-matrix.
```

The contributors file need to be retired, but not today.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ca4566ec3eee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.