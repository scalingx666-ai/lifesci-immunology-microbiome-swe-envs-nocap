# Issue

**Title:** Fix imgvr blast filter - GFF virify_quality validation issue

## Description

I've also:
- Upgraded the requirements-test.txt packages
- Replaced some SeqIO.parse with the filename to a file handle; I was getting "ResourceWarning: unclosed file <_io.TextIOWrapper name='.../final-viral-combined.fa' mode='rt' encoding='UTF-8'>
  for record in SeqIO.parse(final_combined_fa_file, "fasta"):". I don't have the time to look into biopython so I used a context manager to avoid leaving file handlers opened by accident.
- In the blast filter removed a task attemp snippet, IMO it wasn't needed.

Should fix -

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e26ed1590bd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.