# Issue

**Title:** Dom/purgatory

## Description

# Before

```
make acido-frontier-search
python -m search.frontier_search acido/acido-chunk1.fa.gz.sig acido 0.1
loaded 1631 nodes from catlas acido/catlas.csv
loaded query sig data/acido-chunk1.fa.gz
Root containment: 1.0
Root similarity: 0.1331573896353167
Containment of frontier: 1.0
Similarity of frontier: 0.7827926657263752
Size of frontier: 69 of 1631 (4.23%)
Overhead of frontier: 0.21720733427362482
Number of leaves in the frontier: 15
Number of empty catlas nodes in the frontier: 36
Size of the shadow: 193
```

```
make 15genome-frontier-search                                                                                                                          486ms
python -m search.frontier_search data/15genome.5.fa.sig 15genome 0.1
loaded 40322 nodes from catlas 15genome/catlas.csv
loaded query sig 15genome.5.fa
Root containment: 1.0
Root similarity: 0.09282589676290463
Containment of frontier: 1.0
Similarity of frontier: 0.900679117147708
Size of frontier: 1134 of 40322 (2.81%)
Overhead of frontier: 0.09932088285229201
Number of leaves in the frontier: 271
Number of empty catlas nodes in the frontier: 541
Size of the shadow: 2744
```

# After 

```
make acido-frontier-search                                                                                                                     2746ms
python -m search.frontier_search acido/acido-chunk1.fa.gz.sig acido 0.1
loaded 1631 nodes from catlas acido/catlas.csv
loaded query sig data/acido-chunk1.fa.gz
Root containment: 1.0
Root similarity: 0.1331573896353167
Containment of frontier: 1.0
Similarity of frontier: 0.7827926657263752
Size of frontier: 69 of 1631 (4.23%)
Overhead of frontier: 0.21720733427362482
Number of leaves in the frontier: 15
Number of empty catlas nodes in the frontier: 36
Size of the shadow: 721
```

```
make 15genome-frontier-search                                                                                                               419ms
python -m search.frontier_search data/15genome.5.fa.sig 15genome 0.1
loaded 40322 nodes from catlas 15genome/catlas.csv
loaded query sig 15genome.5.fa
Root containment: 1.0
Root similarity: 0.09282589676290463
Containment of frontier: 1.0
Similarity of frontier: 0.900679117147708
Size of frontier: 1134 of 40322 (2.81%)
Overhead of frontier: 0.09932088285229201
Number of leaves in the frontier: 271
Number of empty catlas nodes in the frontier: 541
Size of the shadow: 23965
```

# with purgatory

```
make acido-frontier-search-optimized                                                                                                           2568ms
python -m search.frontier_search acido/acido-chunk1.fa.gz.sig acido 0.1  --purgatory
loaded 1631 nodes from catlas acido/catlas.csv
loaded query sig data/acido-chunk1.fa.gz
Root containment: 1.0
Root similarity: 0.1331573896353167
Containment of frontier: 1.0
Similarity of frontier: 0.9024390243902439
Size of frontier: 66 of 1631 (4.05%)
Overhead of frontier: 0.0975609756097561
Number of leaves in the frontier: 12
Number of empty catlas nodes in the frontier: 36
Size of the shadow: 721
```

```
make 15genome-frontier-search-optimized                                                                                                        2407ms
python -m search.frontier_search data/15genome.5.fa.sig 15genome 0.1 --purgatory
loaded 40322 nodes from catlas 15genome/catlas.csv
loaded query sig 15genome.5.fa
Root containment: 1.0
Root similarity: 0.09282589676290463
Containment of frontier: 1.0
Similarity of frontier: 0.9498657117278424
Size of frontier: 1095 of 40322 (2.72%)
Overhead of frontier: 0.050134288272157566
Number of leaves in the frontier: 232
Number of empty catlas nodes in the frontier: 541
Size of the shadow: 23965
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a211625bc985`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.