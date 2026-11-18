# Issue

**Title:** Pangenome input structure database

## Description

We're getting there. 6th PR related to the integration of ColabFold (#2754).
This time we introduce a big new change: pangenome as a new input type!
Why? To later compute structure-based pangenome, and to visualize prot structure in the pangenome interactive interface.

Here is how it looks like:
```bash
# every gene of the selected clusters
anvi-gen-structure-database --pan-db PAN.db -g GENOMES.db \
    --gene-cluster-ids GC_00000068,GC_00000088 -o STRUCTURE.db

# a single representative gene per cluster
anvi-gen-structure-database --pan-db PAN.db -g GENOMES.db \
    --gene-cluster-ids GC_00000068 --select-representative -o STRUCTURE.db
```

Here we have a new PangenomeSource in structureops.py. With contigs.db, the protein id == gene caller id; here the protein id is a integer and the protein table links it to a genome name, gene caller id and gene cluster id.

AA sequence come from the genomes-storage db (therefore required input).

Two selection modes: all proteins of selected gene clusters, or representative sequence (#2765, a protein pick not a consensus prot).

Works with `anvi-gen-structure-database` and `anvi-update-structure-database`.

My only issue is that the flag `-p` was already used by MODELLER's parameter `--percent-cutoff`. So right now you need to use `--pan-db` full flag to pass a pan db. A bit annoying. I haven't decided if I can/should retire `-p` from `--percent-cutoff` into the short flag for pangenome. I cannot find any reproducible workflow or documentation that uses the original `-p`, so I think I could be safe replacing it, but it feels wrong too. I'll ask the wiser people when I get the chance.

We also have a new test! Mirroring the unusual test `run_component_tests_for_SCVs_SAAVs_structure.sh`, meaning you run it directly in the `tests` dir, not as part of the self tests. Debatable I agree and I'm ready to hear opinions.

Also, right now you cannot bring external structures when in pangenome mode. I think we should be able. But for now, we will be happy with what we have. The tests are running but I want to run it on a real pangenome first. Then we'll see if we allow external structures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc69d40ba804`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.