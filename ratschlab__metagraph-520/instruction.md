# Issue

**Title:** support conversion from RowDiff<Mutli-BRWT> to RowDiff<RowFlat>

## Description

Example:
```bash
./metagraph build -k 31 -o test ../tests/data/transcripts_100.fa

./metagraph annotate -v -i test.dbg --anno-header -o annotation ../tests/data/transcripts_1000.fa
./metagraph transform_anno -v -p 36 --anno-type row_diff --row-diff-stage 0 -i test.dbg -o annotation_rd --mem-cap-gb 300 annotation.column.annodbg
./metagraph transform_anno -v -p 36 --anno-type row_diff --row-diff-stage 1 -i test.dbg -o annotation_rd --mem-cap-gb 300 annotation.column.annodbg
./metagraph transform_anno -v -p 36 --anno-type row_diff --row-diff-stage 2 -i test.dbg -o annotation_rd --mem-cap-gb 300 annotation.column.annodbg

./metagraph transform_anno -v -p 0 --anno-type row_diff_brwt -i test.dbg -o annotation --mem-cap-gb 300 annotation.row_diff.annodbg
./metagraph transform_anno -v -p 0 --anno-type row_diff_flat -i test.dbg -o annotation --mem-cap-gb 300 annotation.row_diff.annodbg

./metagraph transform_anno -v -p 0 --anno-type row_diff_flat -i IGNORED -o annotation_converted annotation.row_diff_brwt.annodbg
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e5f05abcd20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.