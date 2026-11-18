# Issue

**Title:** Add makedb mode to pre-generate mapping databases

## Description

Add a new 'coverm makedb' subcommand that builds persistent mapping
indexes (databases) from reference genome or contig FASTA files, so they
can be reused across multiple 'coverm contig'/'coverm genome' runs
without re-indexing.

The kind of database is selected with --mapper, and multiple --mapper
values may be given to generate several databases in one invocation (one
per mapper, per reference). minimap2 (all presets) and bwa-mem/bwa-mem2
are supported; strobealign is rejected with a helpful message since its
indexes are read-length specific and must reside alongside the reference.

The minimap2 database is written as <ref>.<mapper>.mmi and can be fed
back in via 'coverm contig -r <db>.mmi --minimap2-reference-is-index'.

- Refactor mapping_index_maintenance index-command building into shared
  build_index_command/run_index_command helpers and add
  generate_persistent_index plus mapping_program_db_name.
- Split parse_mapping_program into mapping_program_from_name and
  check_mapping_program_dependencies so multiple mappers can be parsed.
- Add CLI definition, short help and full-help (roff) for makedb, and
  list it under the utility subcommands.
- Add functional tests and document the mode in the README and release.sh
  doc generation.

Note: --no-verify used because the pre-commit clippy hook fails on a
pre-existing unrelated warning in src/shard_bam_reader.rs under the
current clippy version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cff2fe348843`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.