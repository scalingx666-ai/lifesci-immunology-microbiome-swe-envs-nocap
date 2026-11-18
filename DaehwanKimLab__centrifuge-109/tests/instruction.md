# Issue

**Title:** centrifuge-kreport: process "no rank" assignments

## Description

Currently, `centrifuge-kreport` ignores "no rank" taxonomic assignments, due to the way the `centrifuge` output is processed.  This contributes to the discrepancy in read counts, which some users have noted (e.g. ).

For example, this `centrifuge` output:
```
readID	seqID	taxID	score	2ndBestScore	hitLength	queryLength	numMatches
read1	no rank	1	3217	0	95	146	1
read2	no rank	1	64	0	23	150	1
```
currently leads to this `centrifuge-kreport` output, which looks like 0 reads were processed:
```
  0.00	0	0	U	0	unclassified
```

The debugged version produces this:
```
  0.00	0	0	U	0	unclassified
100.00	2	2	-	1	root
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91dfff9f02c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.