# Issue

**Title:** Raise errors instead of calling `sys.exit()` in `diamond.py`

## Description

`diamond.py` stopped the program with `sys.exit()` when checkm2 or DIAMOND failed. A library module shouldn't end the process itself, and those calls made the code harder to test. It now raises an exception, which the CLI turns into an exit code.

### Changes
- New `DiamondError` exception in `diamond.py`, with an `exit_code` attribute. It replaces the `sys.exit()` calls in `get_checkm2_db()`, `run()` and `get_contig_to_kegg_id()`.
- `main.py` catches `DiamondError`, logs the message and exits with its code. The behaviour is unchanged: same message, exit code 1, or 3 when the DIAMOND result file is empty.
- -`check_tool_exists()` raises `DiamondError` too, so a missing `diamond` binary logs a clear message and exits with code 1 instead of showing a traceback.

### Tests
- The diamond unit tests now expect `DiamondError` instead of `SystemExit`.
- A new CLI test checks that a `DiamondError` ends the run with its exit code and a logged message.

This has been implemented with the help of Claude Code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10226fc534a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.