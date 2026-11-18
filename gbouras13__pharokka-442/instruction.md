# Issue

**Title:** Fix path traversal via unsanitised contig/protein headers in --split

## Description

split_fasta_singles() and split_faas_singles() build output filenames directly from user-controlled FASTA header content (SeqRecord.id -- the first whitespace-delimited token of the header line), with no sanitisation:

    with open(os.path.join(single_fastas, contig + ".fasta"), "w") as f:

A crafted header such as '>../../../../tmp/pwned' becomes the contig id, and the resulting path escapes single_fastas/ entirely -- writing wherever the traversal points, subject to the process's own filesystem permissions. Both --split (split_fasta_singles) and the protein-splitting path (split_faas_singles) share the identical pattern.

Fix: two small helpers in post_processing.py --
  * _safe_filename_component() strips everything but [A-Za-z0-9._-] and any leading dots, so a header can no longer become '..', a hidden file, or contain a path separator.
  * _safe_join() is defense in depth on top of that: it resolves the final path and raises if it would land outside the intended directory, catching anything the character filter didn't anticipate. Both call sites now route through these before opening a file.

Verified against a real bioconda pharokka=1.10.1 install (not just read): the original '../../../../tmp/pwned'-style header no longer escapes the output directory and the file lands safely inside single_fastas/ instead, an ordinary accession-style contig id like 'NC_043029.1' passes through completely unchanged (no false positives), and the module still imports cleanly with 'pharokka --version' unaffected.

Found while building https://phage-annotation.org, a web server wrapping pharokka -> phold -> phynteny_transformer. Not exploitable there specifically -- that server rewrites every contig id to a canonical ctg_NNNN form before pharokka ever sees it -- but it's a real bug for anyone piping untrusted uploads into --split directly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `996f7c31a0e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.