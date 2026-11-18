# Issue

**Title:** Check `anvi-draw-kegg-pathways` package dependencies before their import

## Description

`anvi-draw-kegg-pathways` has a `check_package_dependencies` that imports `Bio`, `reportlab`, and `fitz` and raises a `ConfigError` naming whichever are missing. It was called from `main()` — after the module's own from `keggmapping import …` had already run. `keggmapping.py` imports `fitz` on its line 6 and reaches `reportlab` through `kgml.py`, so a missing package killed the program during import and the message was unreachable. This PR moves the check above that import, which is the only place it can run in time. It now runs while the module is being imported by the CLI script, before `main()` and its `except ConfigError` exist, so it prints the error and exits itself — raising there would reach the user as a traceback with the message tacked on the end.

Also, the message drops `pip install -r requirements.txt`, which has pointed at a file that does not exist since `requirements.txt` and `setup.py` were removed.

'Bio' stays in the checked tuple but cannot fire, before or after this change: `biopython` is already pulled in one line earlier by from `anvio.argparse import ArgumentParser` → `utils.py:32`, whose own `except ModuleNotFoundError` exits with the generic "conda environment … not properly initialized" warning. Covering it would mean hoisting the check above the rest of the anvi'o imports.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a1fb0f411db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.