# Issue

**Title:** Validate SSHash input before building, keep temp files out of CWD

## Description

## Problem

`metagraph build --graph sshash -k 21 transcripts_100.fa` writes 1 GiB `sshash.tmp.run_*.minimizers.N.bin` files into the CWD without bound (about 1.4 TB in 20 minutes).

## Root cause (from reading the code)

SSHash's FASTA parser reads each record as **one header line plus one sequence line** and checks neither (only `assert(n >= k)`, which is compiled out in Release). `transcripts_100.fa` is wrapped at 60 chars, and some tail lines are only 1–5 chars long. So header and sequence lines get paired out of step, and eventually a line shorter than k is taken as a sequence. Then `sequence_len - k + 1` underflows in `compute_minimizer_tuples`, the loop runs ~2^64 times, and every full buffer (1 GiB with 4 threads) is flushed to a new temp file. It has nothing to do with `m` selection. Contigs work because they are written one sequence per line.

## Fix

- **sshash submodule** → ratschlab/sshash `master` `98efeb8` (on top of #684's `013f8f9`). The same parser changes are upstream as jermp/sshash#105. `encode_strings.cpp` now:
  - reads wrapped FASTA: a record's sequence runs until the next `>` header, so `transcripts_100.fa` builds instead of looping;
  - throws `std::runtime_error` on: a first line that is not a `>` header (e.g. FASTQ); a sequence shorter than k; a missing final newline (that record used to be dropped silently); a header followed by another header or by the end of the file (also dropped silently); a character outside the alphabet, e.g. `N` in DNA (used to be encoded silently as some other base). The alphabet check is one table lookup per input character, about 0.35 s per GiB.
- **Duplicate k-mer check.** SSHash doesn't support duplicate k-mers: a repeated k-mer gets several node indexes, and a lookup finds only one of them. Raw reads now fail with a clear `std::invalid_argument` instead of producing an inconsistent graph. The other graph representations deduplicate k-mers on insertion, so this is SSHash-only. The check is folded into the existing succ/pred pass: a node reached from its predecessor was already found at its own index by the neighbour lookup, so only the other nodes (unitig starts and block starts) get one extra `lookup`. That pass also used to skip the last node, which is fixed here. In canonical mode the index after the last node is the reverse complement of node 1, so the last node never gets the next-index shortcut.
- **Temp files** go to `utils::create_temp_dir(get_swap_path(), "sshash")`: the `--disk-swap` directory if given, otherwise `./`, the same fallback as the other `get_swap_path()` users. SSHash used to write its run files straight into the CWD. The directory is removed after the build, and also when the build throws.

## Tests

`tests/graph/test_dbg_sshash.cpp` covers each rejection, a wrapped record, and one-sequence-per-line input. The fixture lowers `RLIMIT_FSIZE` to 64 MiB, so a regression dies with SIGXFSZ instead of filling the CI disk (it may still use a few GB of RAM first). The sshash errors are `std::runtime_error` and the duplicate check throws `std::invalid_argument`, so the tests catch `std::exception` and check the message.

Verification: DNA and Protein `metagraph` + `unit_tests` compile locally with g++-15 (Release). The sshash test passes locally with the file size capped, and wrapped copies of two sshash test inputs build indexes byte-identical to the unwrapped ones. The metagraph tests were **not run locally**; I'm relying on CI. I did not reproduce the runaway build locally.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a4e4b81ea47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.