# Issue

**Title:** add dask and jellyfish to conda_env

## Description

```
./rgi database --version
Traceback (most recent call last):
  File "./rgi", line 2, in <module>
    from app.MainBase import MainBase
  File "/home/hunglin/p5/projects/forks/rgi/app/MainBase.py", line 16, in <module>
    from app.BWT import BWT
  File "/home/hunglin/p5/projects/forks/rgi/app/BWT.py", line 9, in <module>
    import dask.dataframe as dd
ModuleNotFoundError: No module named 'dask'
```

```
./test.sh
./test.sh: line 18: jellyfish: command not found
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d850e30d48d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.