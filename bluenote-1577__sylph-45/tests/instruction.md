# Issue

**Title:** Add -r option (list of single-end fastq files) to profile

## Description

Hi @bluenote-1577,

I’ve added an option to handle single-end FASTQ files in sylph profile.

It is already possible to do this with the following command:
`sylph profile db.syldb  file.fastq.gz `

However, since file format detection relies on the file extension, it does not work when the input is a file descriptor, for example, when multiple FASTQ files are concatenated on the fly:
```
sylph profile db.syldb  <(zcat file.fastq.gz file2.fastq.gz)  -o test
2025-02-25T15:05:54.876Z INFO  [sylph::contain] Obtaining sketches...
2025-02-25T15:05:54.876Z WARN  [sylph::contain] /dev/fd/63 file extension is not a sketch or a fasta/fastq file.
2025-02-25T15:05:54.876Z ERROR [sylph::contain] No read files found; see sylph query/profile -h for help. Exiting
```

While waiting for #35 to be implemented, this seems like a good alternative to me.

What do you think?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c92b8c6e64a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.