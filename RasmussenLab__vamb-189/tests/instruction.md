# Issue

**Title:** Fix FASTA parsing with Windows newlines

## Description

When iterating lines of a file, Python includes the trailing `\n`, such that Windows lines ends with `\r\n`. Regex considers `$` to mean the end of the line, not end of the string. Vamb's header regex check did not take the trailing newline into account, but this happened to not matter since
* Only the identifier was used in Vamb's internals, so the newline in the description was not noticed, and
* It still passed the regex header check, as the regex matching stopped at the `\n` character. However, `\r\n` threw a wrench in all that.
Fix it by simply removing the trailing `\r?\n` in the FASTA parser.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79919d8c43dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.