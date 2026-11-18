# Issue

**Title:** Deprecated QMAX as a preprocessor defined variable.

## Description

The functions compute_lambda, b_make_positional_substitution_df,
b_make_transition_by_quality_matrix, & b_compare are modified to accept
qmax as a local parameter.

The main function dada now no longer accepts QMAX as a variable. QMAX
is now specified by the column length of err (the Error Matrix). When
the maximum Quality Score in derep exceeds the column length of err, err
is extended by repeating the last column and a verbose warning is thrown.
When Quality Scores exceed 45 a warning is thrown, when Quality Scores
exceed 62, execution is stopped.

All lines of code that I 'subtracted' are simply commented-out.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7def3cd77990`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.