# Issue

**Title:** fix: fix handle of "6" shape path

## Description

will fix #43

## background
in the issue, queries are extended as follow pattern:
![1368a2bafc107fc2e242dd719e03867](https://github.com/user-attachments/assets/f3536479-4ce3-4c3f-9533-063c80d4cb8a)

and the environment is:
```python
query_set = frozenset((           "AcMG_5518", "AcMG_12242", "AcMG_3793", "AcMG_755", "AcMG_9925", "AcMG_9528"))
contig2assembly = {
    "AcMG_3793" : {"AcMG_925032", "AcMG_5518", "AcMG_12242", "AcMG_3793"},
    "AcMG_755"  : {"AcMG_925032", "AcMG_5518", "AcMG_12242", "AcMG_3793", "AcMG_755", "AcMG_9925"},
    "AcMG_12242": {"AcMG_925032"} | query_set,
    "AcMG_5518" : {"AcMG_925032"} | query_set,
    "AcMG_9925" : {"AcMG_925032"} | query_set,
}
path_circular_potential=frozenset({"AcMG_755"})
contig_link_no_pe=frozenset({"AcMG_9528"})
```

## bug analysis
in this case, a query (`AcMG_9528`) exists as an arm of a ring (represenated by `AcMG_755`). In this case, both the ring and the longer path should be marked as failed. A shorter not-ring path inner the failed ring can be reported instead (but failed for bug)

## fixes:
1. fix the bug report here. Now the shortest common path are kept.
2. make code easier to read (seperate functions and NamedTuple)
3. fix other bugs via adding tests

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58c8abfba9d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.