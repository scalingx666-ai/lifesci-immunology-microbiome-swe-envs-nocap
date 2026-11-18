# Issue

**Title:** contig_taxonomic_assign.py updated

## Description

@mberacochea, @guille0387 did changes to the voting system that we will now also use in the final manuscript version. 

I think it's best to merge this into `dev` and then you can merge this into `master` (or before into `cwl-docker`)? 

Some of the other branches that are currently open (`no-pprmeta`, `pprmeta-score`, `no-bitscore-filter`) where more for testing purposes and need not be merged (now). 

Would be great if we can get a new release at some point! :) 

btw: my EBI acc (email) is deactivated so I don't have any access to slack anymore. But please feel free to contact me via email or github issues ;)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cdf297c7be4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.