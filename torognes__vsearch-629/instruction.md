# Issue

**Title:** Fix off-by-one in MSA consensus ;length= output

## Description

print_consensus_sequence() passed cons_v.size() as the sequence length to fasta_print_general(), but cons_v is sized conslen + 1 — the extra slot holds the '\0' terminator. With --consout --lengthout this made the ;length= field of every cluster's consensus one larger than the actual consensus (the sequence body itself is unaffected, since it is printed via "%.*s" and stops at the embedded NUL).

Pass cons_v.size() - 1 so the reported length matches the true residue count, consistent with every other fasta_print_general() caller. cons_v always contains at least the terminator, so the subtraction is safe.


Claude-Session: https://claude.ai/code/session_01H6v7rX4pGLAL5BT2EWWxMM

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1477f5f6f00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.