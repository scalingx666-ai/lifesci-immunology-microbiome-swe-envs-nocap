# Issue

**Title:** Structure prediction in the contigs workflow

## Description

First step of the workflow integration for #2754: the contigs workflow can now generate a structure database for each contigs database with anvi-gen-structure-database. Pangenomics and metagenomics will follow in their own PRs.

Structure prediction is off by default; set run: true for the rule anvi_gen_structure_database in the config to turn it on. The workflow writes one structure database per genome to a new directory, 03_STRUCTURE. These databases are their own targets, separate from annotate_contigs_database.done, so a long prediction does not hold up the rest of the workflow or the workflows that inherit from contigs. Annotation rules writing to the contigs database later do not trigger a new prediction either.

By default, the workflow predict a structure for ALL proteins. You can optionally have a list of gene caller id in the fasta-txt which will be the list of genes-of-interest. Because gene caller ids only exist once a contigs database is built, the expected use is: run the workflow, pick your genes, add the column, turn on structure prediction, and run the workflow again. Or you are providing external gene calls and you know what you are doing. 

With a local ColabFold database, split_msa_and_predict: true splits the prediction into two jobs, colabfold_msa (--only-msa, CPU) and colabfold_predict (--only-predict, GPU), using the --dump-dir checkpoint from #2760. The MSA directory is temporary and is removed once the structure database is built. The rules that predict with ColabFold declare the Snakemake resource gpu=1; and you can map it onto your own scheduler.

Internally, this is a new StructureModule (anvio/workflows/structure/) with its own params.json and rules. ContigsDBWorkflow inherits it, so pangenomics and metagenomics already get the config entries and their own structure directories (04_STRUCTURE and 10_STRUCTURE), but nothing runs there yet.

And we also have a new workflow test, run_workflow_tests_for_structure.sh. It runs MODELLER by default, set COLABFOLD_CONDA_ENV to run ColabFold, and add COLABFOLD_DB to test the split mode.

I need to push this branch/PR to then test it on the HPC properly and will not merge before a few tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fba3e1abce16`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.