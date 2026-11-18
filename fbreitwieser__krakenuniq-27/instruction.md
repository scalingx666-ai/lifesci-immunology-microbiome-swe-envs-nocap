# Issue

**Title:** Remove additional curly brackets

## Description

I get unmatched right curly bracket in the krakenuniq script when I try to package for bioconda. I think this addition curly bracket should be removed. 

Error log from Bioconda build: 
```
+ krakenuniq --version
KrakenHLL version 0.5.1
Copyright 2017-2018, Florian Breitwieser (fbreitwieser@jhu.edu)
Copyright 2013-2017, Derrick Wood (dwood@cs.jhu.edu) for Kraken
+ krakenuniq-build --version
String found where operator expected at /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build line 367, near "$ENVP"KRAKEN_MIN_CONTIG_SIZE""
	(Missing operator before "KRAKEN_MIN_CONTIG_SIZE"?)
Global symbol "$ENVP" requires explicit package name (did you forget to declare "my $ENVP"?) at /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build line 367.
syntax error at /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build line 367, near "$ENVP"KRAKEN_MIN_CONTIG_SIZE""
Unmatched right curly bracket at /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build line 370, at end of line
syntax error at /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build line 370, near "}"
Execution of /opt/conda/conda-bld/krakenuniq_1535612903373/_test_env_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold_placehold/bin/krakenuniq-build aborted due to compilation errors.
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5932a3f2112`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.