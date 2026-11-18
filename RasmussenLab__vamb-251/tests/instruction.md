# Issue

**Title:** Refactor binsplitting

## Description

There are multiple problems with the way we do binsplitting now, which I would like to address is this larger PR:
* We either output split bins or unsplit bins, where it would be more useful to output both, if possible (#237).
   - In this PR, both files are always written if binsplitting takes place.
* We default to no binsplitting, even though we know this produces worse output. Ideally, we'd like for Vamb's defaults to be optimal.
   - In this PR, we default to binsplitting with `'C'`.
* If users pass in a wrong binsplit separator, e.g. by mindlessly copy-pasting `-o C` into the command without realising what it implies about the naming scheme of the identifiers, then Vamb errors only at the clustering step after training. Ideally, this would error already when reading in the FASTA file.
   - In this PR, it errors when parsing the FASTA file if the separator is not found, UNLESS the user did not specify any separator and it just defaulted to 'C'. In this case, it will warn the user, and then disable binsplitting
   - The error message is improved in this PR
* The logic of binsplitting is too complicated, because binsplitting takes place at multiple different levels: Immediately after instantiating the clusterer, when writing the cluster file, or when writing the bins file.
   - In this PR, only binsplit immediately before writing to files.
   - Also, in this PR, the printing functions should not binsplit. Instead, binsplit the clusters, then print them

Further,
* I have removed the `-i` option. This is not generally useful. We should instead output total bin size and other bin statistics to users and let them decide (#240)

### To do
- [x] Refactor the clustering and writing of clusters in `__main__.py` to deduplicate code
- [x] Address TODOs
- [x] Make sure the program runs normally
- [x] ....and respects `-o X` and `-o `
- [x] ...and respects `-c X`
- [x] Make tests pass

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2e51b3e5ae4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.