# Issue

**Title:** Pangenomics workflow fix

## Description

There was an error in the pangenomics workflow where the output was being written to a directory instead of a db. This was a recent flag change in anvi'o that was not reflected in the workflow. The command run was `anvi-self-test --suite workflow-pangenomics -T 40 --output-dir test_output2` from the `anvio/tests/` directory.

Additionally, there were two errors in the component testing workflow for pangeomics where some of the testing data was not included but still being referenced.

Changes:
- Changed the output of the rule in the `anvi_pan_genome` rule to be {output} instead of {params.output_dir}.
- Changed the "fasta_txt": "fasta.txt" to "fasta_txt": "five-genomes-fasta.txt" in the `anvio/tests/sandbox/workflows/pangenomics/config.json` file.
- Removed broken cp for data that doesn't exist.

These issues have been addressed and the workflow now runs using the changes above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06b13be4d09e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.