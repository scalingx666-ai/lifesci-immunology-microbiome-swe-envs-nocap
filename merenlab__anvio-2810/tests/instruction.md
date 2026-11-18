# Issue

**Title:** safer pip reinstall suggestion

## Description

When `AnvioPrograms.sanity_check()` finds a mismatch between the `anvi-*` entry points declared in `pyproject.toml` and the `anvi-*` programs on `$PATH`, it prints the "ANVIO ENVIRONMENT IS CONFUSE" warning and recommends:
```
pip install -e . --force-reinstall --upgrade
```

This PR changes that recommendation to plain `pip install -e .`, with `pip install -e . --force-reinstall --no-deps` as a fallback.

We had already noticed a few times (during the hackathon) that the `--force-reinstall` was breaking things more than we want. The simple `pip install -e .` will re-install anvi'o and the new command line will show up, no need to re-install all dependencies.

Let me know if I missed something here by updating that recommendation. It is not the first time I though about changing it but recent issue on our shared anvi'o env on the HPC let me believe that the `--force-reinstall` could be one cause of observed issues.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0224aa76f22`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.