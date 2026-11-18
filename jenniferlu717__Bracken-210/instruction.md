# Issue

**Title:** Update combine_bracken_outputs.py

## Description

update combine_bracken_outputs.py due to following error 
```
PROGRAM START TIME: 12-07-2022 21:22:10
Processing Output File wastewater_SRR19419489:: Sample wastewater_SRR19419489
Processing Output File wastewater_SRR19419488:: Sample wastewater_SRR19419488
Traceback (most recent call last):
  File "/data/gpfs/assoc/bch709-3/wyim/metagenome/bracken/analysis_scripts/combine_bracken_outputs.py", line 151, in <module>
    main()
  File "/data/gpfs/assoc/bch709-3/wyim/metagenome/bracken/analysis_scripts/combine_bracken_outputs.py", line 133, in main
    taxid = sample_counts[name].keys()[0]
            ~~~~~~~~~~~~~~~~~~~~~~~~~~^^^
TypeError: 'dict_keys' object is not subscriptable
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88b77381684e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.