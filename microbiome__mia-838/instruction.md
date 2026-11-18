# Issue

**Title:** Tidy ibdmdb data

## Description

1. Kept the sample metadata names as they are in the original table
2. Splitted data based on taxonomy. I kept the main TreeSE as it is currently, but added agglomerated data to altExps. Good to note that joint-RPCA tests etc are based on the following data:

```
> rowData(mae[[1]])
DataFrame with 459 rows and 8 columns
                                                                                                                              kingdom
                                                                                                                          <character>
k__Archaea                                                                                                                    Archaea
k__Archaea|p__Euryarchaeota                                                                                                   Archaea
k__Archaea|p__Euryarchaeota|c__Methanobacteria                                                                                Archaea
k__Archaea|p__Euryarchaeota|c__Methanobacteria|o__Methanobacteriales                                                          Archaea
k__Archaea|p__Euryarchaeota|c__Methanobacteria|o__Methanobacteriales|f__Methanobacteriaceae                                   Archaea
...                                                                                                                               ...
k__Viruses|p__Viruses_noname|c__Viruses_noname|o__Caudovirales|f__Siphoviridae                                                Viruses
k__Viruses|p__Viruses_noname|c__Viruses_noname|o__Caudovirales|f__Siphoviridae|g__C2likevirus                                 Viruses
k__Viruses|p__Viruses_noname|c__Viruses_noname|o__Caudovirales|f__Siphoviridae|g__C2likevirus|s__C2likevirus_unclassified     Viruses
k__Viruses|p__Viruses_noname|c__Viruses_noname|o__Caudovirales|f__Siphoviridae|g__Siphoviridae_noname                         Viruses
k__Viruses|p__Viruses_noname|c__Viruses_noname|o__Viruses_noname                                                              Viruses
```

i.e., --if I recall correctly--same observation is counted multiple times. Might not be biologically valid...

@antagomir

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af684cb7328d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.