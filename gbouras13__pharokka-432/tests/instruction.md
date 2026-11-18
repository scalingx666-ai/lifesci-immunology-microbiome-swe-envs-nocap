# Issue

**Title:** Fix test mutating committed data and duplicate minced GFF headers

## Description

test_external_commands.py's testGenePred class wrote gene-predictor outputs into the committed SAOMS1_Output/ reference dir. Combined with MinCED opening its GFF output in append mode, every pytest run appended another "##gff-version 3" line to pharokka_minced.gff, leaving a dirty working tree.

- Convert testGenePred to a plain pytest class so the tmp_dir fixture is injected; write all run_* outputs to tmp_dir instead of SAOMS1_Output.
- run_minced now removes any stale _minced.gff/_minced_spacers.txt before invoking MinCED, so exactly one header is emitted per run.
- Restore pharokka_minced.gff to a single-header state.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `357ee05a15a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.