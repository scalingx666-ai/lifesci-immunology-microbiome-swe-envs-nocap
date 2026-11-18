# Issue

**Title:** Improved multithreading of anvi-run-kegg-kofams (and a bonus addition to the HMMER driver)

## Description

This PR addresses two performance bottlenecks with `anvi-run-kegg-kofams`. Previously, only the HMMER run was multithreaded, while the parsing/filtering of HMM hits (and the bitscore heuristic) was done entirely by the main process:

    FASTA → split(N) → [workers: run HMM] → merge HMMER outputs → parse → filter → heuristic → store
                                             ←——————— main process, serial ———————————————→

This was extremely inefficient, especially for large datasets. The improved strategy parallelizes the parsing through heuristic steps as well:

    FASTA → split(N) → [workers: run HMM + parse + filter + heuristic] → merge annotations → store
                        ←————————— all parallel ————————————→              ← main process →

This change should also improve the memory usage of this program, because the main process no longer has to work with all HMM hits returned by all child processes.

At the same time, I also added a new (optional) parameter for total number of sequences to the HMMER driver to allow setting -Z and -domZ.

## A new AnnotationWorker class

To accomplish this, this PR introduces a new worker class, `AnnotationWorker` (in `annotate.py` module), that:
  - receives everything it needs at construction time: partition file (of genes to process), HMM paths, ko_dict, stray ko dict (of no-threshold KOs, which are still called stray KOs internally in the code) if applicable, dictionaries of info loaded from the modules DB, heuristic params, flags, a log file path, and total number of gene sequences in the contigs db
    - most of the dictionaries are passed via a SharedMemory object to avoid copying them multiple times for each worker
  - runs (on the input partition of genes):
    - writes its own progress output to the log file
	- calls single-threaded HMMer for regular KOfam run
	- calls single-threaded HMMer for nt-KO run if applicable
	- parses all HMMer outputs 
	- filters by bitscore (unless `--keep-all-hits`)
	- applies heuristic (unless `--keep-all-hits` or `--skip-bitscore-heuristic`)
	- puts result dict on queue
  - has one try-except clause around the whole body; exceptions go on the queue just as they did when we were using `hmmer_worker`

Here is the main process design in more detail, which is implemented in `process_kofam_hmms` in the `RunKOfams` class:
  1. Splits FASTA once → N partition files
  2. Pre-fetches data from the KEGG Module DB
  3. Spawns N `AnnotationWorker` processes (via multiprocess.Process), passing each the aforementioned files to each one
  4. Shows coarse progress to the terminal: "Completed X of N partitions"
  5. Collects compact annotation dicts from workers as they finish
  6. Merges results from all workers and stores to DB

I was concerned about the memory overhead of step 3, since several large-ish dictionaries are passed to each worker and depending on how the worker processes are spawned, these could be copied. At least the dictionary size is bounded by the KEGG data size (number of KOs, number of modules), so this space won't grow -- however, it still seems a waste to copy this unchanging data. So instead of passing copies of these dictionaries to each worker, the new implementation actually uses a `SharedMemory` object from the `multiprocessing` library, similar to @FlorianTrigodet's recent memory-saving update to the profiler ().

Side note: the HMMER driver spawns child processes, even when the number of threads is 1. Which means that the main process spawns <num-threads> children as AnnotationWorker, and then each of those spawns one of its own child processes via the driver. Claude.AI assured me that this doesn't actually impact the total CPU usage of the program, because the AnnotationWorker processes are blocked while the HMMER child process is working. Nice!

## Setting the total number of sequences for `hmmsearch`

One consequence of the restructuring was that the HMMER driver no longer knows about the total number of gene sequences in the contigs database. Previously, we sent the entire (unsplit) file of seqs to the HMMER driver, and allowed that driver to do the splitting and spawning of child processes -- hence, the -Z and -domZ arguments to HMMER were correctly set based on the input file to the driver. But after restructuing via AnnotationWorker, we first split the seqs into partitions and then give each AnnotationWorker (and thus each single-threaded instance of the HMMER driver) only that partition as input. This caused -Z and -domZ to be much smaller (the size of the partition and not the whole sequence set), and yielded e-value differences in my initial tests.

The solution was to add a new parameter to the HMMER driver, `total_number_of_sequences_per_target`. This is a dictionary where the keys are the target file names, and the values are the total number of target sequences. You can provide it in cases like this one, where the partitioning is done _outside_ of the HMMER driver. If its not provided, the default is to identify the number from each input target file, like before.

One thing I tried that didn't work: I thought it would be smart to update the `utils.split_fasta` function so that if you have just 1 thread and therefore need the file to be split into 1 part, it would return the original file instead of "fake-splitting" it to a new temporary file that looks the same as the old one. But unfortunately, having this additional temporary file was necessary; if you just use the original file, subsequent hmmer runs on that file don't work (I think the driver might delete them assuming that they are temporary) -- this manifested in my testing as a failure to annotate nt-KOs. Just so you know the reason for the reverted commit in this branch :)

## Testing
To ensure these changes did not break the functionality of `anvi-run-kegg-kofams`, I had to test that the annotation results were the same before and after the code update, with all reasonable parameter combinations.

Below I include only the results of the final tests I did, though I did several intermediate rounds of testing which helped me to identify and fix problems.

### A small mock dataset

I used Claude.AI to generate a small test database containing 190 'regular' KO genes and 10 'no-threshold' KO genes. Claude automatically downloaded the gene sequences from the KEGG GENES database, with all regular KOs coming from _E. coli_ K-12 and the 10 nt-KOs coming from various other organisms (E. coli, viruses, ag: — "animal gut" entries, and a few protozoa). It downloaded the amino acid sequences and then back-translated them to nucleotide (which I thought was a very roundabout way to go about things, as I'm pretty sure KEGG GENES includes the nucleotide sequence. But I believe it doesn't matter for testing so I left it alone). The genes were cobbled together into fake contigs and those were turned into an anvi'o contigs database, `TEST_KOFAMS.db`.

Here is the script to make the test database:
[make_test_db.py](https://github.com/user-attachments/files/28094889/make_test_db.py)

### Test script
Claude.AI also generated a testing script with 71 different parameter combinations, called `validate_kofams_refactor.py`. It needs to be run using a KEGG snapshot that includes nt-KOs -- I used the latest one (which was the default KEGG data dir on my computer). Here is the script:

[validate_kofams_refactor.py](https://github.com/user-attachments/files/28094948/validate_kofams_refactor.py)

When you run it in `run` mode, it will run `anvi-run-kegg-kofams` with each of the 71 parameter combos and generate a tab-delimited output file of the exported annotations for each one (or report that the combo yielded an error).

Later, you can run it in `compare` mode, giving it two output directories generated by the `run` mode, and it will compare for each parameter combo whether the same annotation output was generated.

### Baseline for testing

Before I made any changes to the codebase, I ran all the parameter combos like this:
```bash
export DEFAULT_KEGG=`python -c "import anvio; import os; print(os.path.join(os.path.dirname(anvio.__file__), 'data/misc/KEGG'))"`

python validate_kofams_refactor.py run \
      --contigs-db TEST_KOFAMS.db \
	  --kegg-data-dir $DEFAULT_KEGG \
	  --output-dir validation/before \
	  --num-threads 4
```

It produces terminal output like the following, which shows which parameter combos were run and that all of them finished successfully:
```
[08:22:55] 71 combinations  --num-threads 4  →  validation/before

  [  1/71] RUN   prog=hmmsearch ... ok  39.9s  473 annotations
  [  2/71] RUN   prog=hmmsearch__skip_brite_hierarchies ... ok  38.7s  275 annotations

(.....)
  [ 70/71] RUN   log_bitscores_keep_all_hits ... ok  91.0s  14015 annotations
  [ 71/71] RUN   log_bitscores_include_nt_kos ... ok  41.8s  482 annotations

Done: 71 passed / 0 failed / 0 skipped
```
And it generated TSV files of the annotation table, one per parameter combo, in the output directory `validation/before`.

### Test outcome 1: the new parameter to the HMMER driver doesn't change the final annotations

I had to make sure that the new parameter doesn't impact the annotation results. This was a bit tricky since I added this parameter after the restructuring was already done. So what I did was to create a new branch off of `master`, `git cherry-pick` the relevant commits for the HMMER driver update, and then run all parameter combos:

```bash
cd ~/software/anvio && git checkout hmmer_num_seq_param && cd -
python validate_kofams_refactor.py run \
      --contigs-db TEST_KOFAMS.db \
      --kegg-data-dir $DEFAULT_KEGG \
      --output-dir validation/hmmer_update_before \
      --num-threads 4
```
All combos were successful, so I was able to compare the baseline annotations to these:
```bash
python validate_kofams_refactor.py compare \
       --before validation/before \
       --after validation/hmmer_update_before
```
And they all matched:

```
Comparing 71 combinations
  before : validation/before
  after  : validation/hmmer_update_before

  OK       [0000] prog=hmmsearch  (471 annotations)
  OK       [0001] prog=hmmsearch__skip_brite_hierarchies  (275 annotations)
(.....)
  OK       [0067] heuristic_bitscore_0.9  (469 annotations)
  OK       [0068] log_bitscores  (471 annotations)
  OK       [0069] log_bitscores_keep_all_hits  (12316 annotations)
  OK       [0070] log_bitscores_include_nt_kos  (480 annotations)

ALL OK: 71 match / 0 mismatch / 0 missing
```

### Test outcome 2: the restructure doesn't change the final annotations

I ran all parameter combos using this branch once it included both the restructuring and the new HMMER driver param (and after I reverted my change to `utils.split_fasta` which caused other issues):
```bash
python validate_kofams_refactor.py run \
      --contigs-db TEST_KOFAMS.db \
      --kegg-data-dir $DEFAULT_KEGG \
      --output-dir validation/hmmer_update_after_revert \
      --num-threads 4
```

The comparison command was:
```bash
python validate_kofams_refactor.py compare \
       --before validation/hmmer_update_before \
       --after validation/hmmer_update_after_revert
```

And everything matched!
```
ALL OK: 71 match / 0 mismatch / 0 missing
```

So I think we are good to go here :)

I haven't quantified the performance improvement because my test data is too small to see meaningful differences. If I have time later, I'll try to run it on a large contigs database and see.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da94e5a883dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.