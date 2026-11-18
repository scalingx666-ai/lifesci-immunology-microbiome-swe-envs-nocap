# Issue

**Title:** Removing and adding some flags for `anvi-estimate-metabolism`

## Description

This PR combines several small improvements to `anvi-estimate-metabolism`.

## No more `--add-copy-number`

Copy numbers of metabolic modules were always being computed behind the scenes, even if the user didn't request them. The old `--add-copy-number` flag merely controlled whether these values were reported. Well. I think copy numbers are equally as important as completeness scores in many cases (and in some cases even more important), and I think they should be treated accordingly.

After this PR, copy numbers are always reported in the program output. The only exception is pangenome input, for which we use annotation presence-absence across gene cluster bins and don't have any annotation copy number data to compute module copy numbers with. What this means is:
- for long format output (the default), the copy number columns will always be included (affected modes: modules, module_paths, module_steps)
- for matrix format output, the copy number matrices will always be produced (ie, for pathwise copy number, stepwise copy number, and per-step copy number)

**Consequences:**
Users no longer have to ask for copy numbers explicitly. On the other hand, historical code using the `--add-copy-number` flag will now fail :)

**Implementation details:**
The `--add-copy-number` flag has been removed for the user, but its internal attribute for the `KeggMetabolismEstimator` class has been replaced with `self.report_copy_number` and `add_copy_number` parameters for functions of the `KeggEstimationAlgorithms` remain. These are used to turn off the copy number output and related terminal messages for the pangenome input case.

## A more explicit name for 'metagenome mode'

It has always been very confusing to people that 'metagenome mode' is optional for metagenomes :) It _actually_ means that we treat each contig in isolation and get per-contig module completeness scores and copy numbers. You can and should run `anvi-estimate-metabolism` on metagenomes without using this mode, especially if you want to compute community-level copy numbers. 

To clarify the situation, this PR does the following:
- renames the `--metagenome-mode` flag. It is now called `--per-contig-estimates`
- removes the metagenomes-txt input option completely (previously the `-M` flag)
- makes the `--per-contig-estimates` flag compatible with external genomes and internal genomes input (as the new alternative to the `-M` flag)

**Consequences:**
This change didn't mostly didn't alter the behavior of the program -- when you run with `--per-contig-estimates`, it is doing the same thing it used to do with `--metagenome-mode`. And running the program with `--external-genomes` and this flag replicates what the old `-M` flag used to do.

The biggest change is that you can now get per-contig estimates for `--internal-genomes`. When you use this combination, each bin in your internal genomes file will be analyzed with per-contig estimates, meaning that you will get per-contig completeness scores and copy numbers for each contig that is contained within a bin in the provided collection. The primary utility of this is to be able to exclude some contigs from your analysis (ie, if you don't care about some fraction of your assembly). Note that it doesn't matter how the contigs are split across bins here, because each one will be analyzed separately -- putting all contigs in one bin is the same as putting each contig into a separate bin (at least in terms of `anvi-estimate-metabolism` output).

**Implementation details:**
While the user-facing parameter has changed its name, the `self.metagenome_mode` attribute is still used internally. `--per-contig-estimates` simply re-directs to this attribute (its destination or `'dest'` in `__init__.py` is the old `metagenome_mode` parameter, so it is basically a synonym). Removing the metagenomes-txt input option simplified the internal logic of the program, especially sanity checks and setup.

## Adding Per-Population Copy Numbers (PPCN) to the output

This change was a request from @jessika-fuessel, who recently implemented a new `--add-per-population-copy-number` flag for another program (). She asked me to adapt this flag for `anvi-estimate-metabolism`, such that the program could automatically estimate the number of populations with single-copy core genes, compute PPCN values, and include these in the output files.

The flag works on individual contigs database or external genomes file input. If long-format output is requested, it adds two new columns to the modules-mode output file (one for pathwise PPCN, and one for stepwise PPCN). If matrix-format output is requested, it creates two additional matrix files. For individual contigs databases, the population estimates are reported on the terminal, and for multi-mode (external genomes), the population estimates for each database are reported as an additional matrix file with suffix `-POPULATION-ESTIMATES.txt` (regardless of whether the rest of the metabolism output is matrix format or not).

**Consequences:**
For users who want to use this optional new flag, they will have to ensure `anvi-run-hmms` is run on their input databases before running `anvi-estimate-metabolism`. There are sanity checks to make sure the SCG annotations exist before doing any metabolism estimation work.

**Implementation details:**
To compute the population sizes, the `NumGenomesEstimator` class is called from the new function `get_num_populations_for_contigs_db()` in the `KeggDataLoader` class (`dbaccess.py`). There is also a new sanity check function for the SCG annotations, `check_scg_hmms_are_present()`, which runs in multi-mode when dbs are being initialized so that we can stop early if any genome is missing these.

To avoid re-computing population estimates for individual contigs databases in multi-mode, we can pass the `KeggMetabolismEstimator` class the num_populations value for the db (set up in `get_args_for_single_estimator`).

The function that computes PPCN is `compute_per_population_copy_number_for_bin` (`algorithms.py`), and it is called only after copy numbers for all modules are finalized (including the adjustment for modules that contain other modules). If the module copy number is NA _or_ the total population size is NA (which can happen if not enough of the relevant SCGs are annotated in a contigs db), then the PPCN value is NA.

## Other things
- the component tests for metabolism have been adjusted to reflect the new flag names and test all new viable input flag combinations
- when you run the program to `--list-available-output-headers`, there were a bunch of hits-mode headers that were marked as belonging to 'kofams' mode (the old name, before we added user-defined metabolism). These have now been updated to reflect that they belong to 'hits' mode.
- @jessika-fuessel is now an author of `anvi-estimate-metabolism` to recognize her intellectual contributions to the program (which have occured throughout its design and implementation process, not just right now -- but better late than never I guess) :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd0c0eba5ac6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.