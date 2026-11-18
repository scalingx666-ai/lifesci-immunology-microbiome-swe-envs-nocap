# Issue

**Title:** Add COMEbin as another optional binner

## Description

Test passes, but it adds a bunch of tmp files at the position of the input assembly:

```bash
ls example/test_short_read_recovery_comebin/assembly.fasta*
example/test_short_read_recovery_comebin/assembly.fasta                                            example/test_short_read_recovery_comebin/assembly.fasta.frag.faa
example/test_short_read_recovery_comebin/assembly.fasta.bacar_marker.2quarter_lencutoff_1001.seed  example/test_short_read_recovery_comebin/assembly.fasta.frag.ffn
example/test_short_read_recovery_comebin/assembly.fasta.bacar_marker.hmmout                        example/test_short_read_recovery_comebin/assembly.fasta.frag.gff
example/test_short_read_recovery_comebin/assembly.fasta.bacar_marker.hmmout.err                    example/test_short_read_recovery_comebin/assembly.fasta.frag.out
example/test_short_read_recovery_comebin/assembly.fasta.bacar_marker.hmmout.out                    example/test_short_read_recovery_comebin/assembly.fasta_lengths.txt
example/test_short_read_recovery_comebin/assembly.fasta.frag.err
```

I guess we could symlink the assembly into the comebin output folder to contain the mess.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `28c63a3f73c0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.