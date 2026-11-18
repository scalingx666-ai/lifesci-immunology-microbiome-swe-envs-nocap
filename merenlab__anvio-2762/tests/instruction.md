# Issue

**Title:** Fix race condition for MODELLER database build

## Description

While working on #2760, ran into this error (component test):

```
:: anvi-gen-structure-database with DSSP ...


CITATION
===============================================
Anvi'o will use 'MODELLER' by Webb and Sali (DOI: 10.1002/cpbi.3) to model
protein structures. If you publish your findings, please do not forget to
properly credit their work.


* Anvi'o found the MODELLER executable mod10.8, so will use it


WARNING
===============================================
Your database is not in binary format. That means accessing its contents is
slower than it could be. Anvi'o is going to make a binary format. Just FYI

Log of binarize_database.py ..................: binarize_database.log
New database .................................: /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.bin

WARNING
===============================================
Your diamond database does not exist. It will be created.

Log of pir_to_fasta.py .......................: pir_to_fasta.log

[DEBUG] `run_command` is running .............: diamond makedb --in /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.fa -d
                                                /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95 -p 1


General info
===============================================
contigs_db ...................................: test-output/one_contig_five_genes.db
contigs_db_hash ..............................: hash67c4a1fa
structure_db_path ............................: test-output/STRUCTURE.db
num_threads ..................................: 2
write_buffer_size ............................: 25
genes_of_interest ............................: None
gene_caller_ids ..............................: 2,4
skip_DSSP ....................................: False
run_mode .....................................: modeller

Modeller parameters
===============================================
modeller_executable ..........................: mod10.8
modeller_database ............................: pdb_95
scoring_method ...............................: DOPE_score
max_number_templates .........................: 5
percent_cutoff ...............................: 30
alignment_fraction_cutoff ....................: 0.7
num_models ...................................: 1
deviation ....................................: 4.0
very_fast ....................................: True
dump_dir .....................................: test-output/RAW_MODELLER_OUTPUT

Log of fasta_to_pir.py .......................: gene_4_fasta_to_pir.log
Target alignment file ........................: 4.pir

WARNING
===============================================
Your diamond database does not exist. It will be created.

Log of fasta_to_pir.py .......................: gene_2_fasta_to_pir.log
Target alignment file ........................: 2.pir

WARNING
===============================================
Your diamond database does not exist. It will be created.

Log of pir_to_fasta.py .......................: pir_to_fasta.log
Log of pir_to_fasta.py .......................: pir_to_fasta.log

[DEBUG] `run_command` is running .............: diamond makedb --in /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.fa -d
                                                /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95 -p 1


[DEBUG] `run_command` is running .............: diamond makedb --in /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.fa -d
                                                /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95 -p 1


[DEBUG] `run_command` is running .............: diamond blastp -q /tmp/tmp9u260z2b -d /fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.dmnd -o
                                                diamond-search-results.txt -t /tmp -p 1 --outfmt 6 qseqid sseqid pident length mismatch gaps gapopen qstart qend sstart send evalue bitscore
                                                --max-target-seqs 100000 --evalue 1e-05



ID 2 Time Report
===============================================
PDB DB loaded ................................: +0:00:42.183783
Converted gene FASTA to PIR ..................: +0:00:00.207136
Total elapsed ................................: =0:00:42.390919

✖ gen_structure_database.py encountered an error after 0:02:22.137324
Traceback (most recent call last):
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/VIRTUAL_ENVS/anvio-flo/bin/anvi-gen-structure-database", line 6, in <module>
    sys.exit(main())
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/terminal.py", line 930, in wrapper
    program_method(*args, **kwargs)
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/cli/gen_structure_database.py", line 37, in main
    structops.StructureSuperclass(args, create=True)._run()
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/structureops.py", line 777, in _run
    self.run_multi_thread(genes_of_interest) if self.num_threads > 1 else self.run_single_thread(genes_of_interest)
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/structureops.py", line 1166, in run_multi_thread
    raise worker_error
  File "/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/structureops.py", line 1118, in run_multi_thread
    raise structure_info
FileNotFoundError: [Errno 2] No such file or directory: '/fs/s6k/groups/agecodatasci/PEOPLE/FlorianTrigodet/SOFTWARE/anvio/anvio/data/misc/MODELLER/db/pdb_95.fa'
```

Turns out it was a race issue where workers build concurrently and delete the file too. Diamond was never checking if the .dmd was actually there after building (fixed that too).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1db8c43c35fc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.