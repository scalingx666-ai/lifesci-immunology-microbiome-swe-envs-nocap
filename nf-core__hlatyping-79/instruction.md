# Issue

**Title:** Patch invalid input index def

## Description

## PR checklist
 - [x] This comment contains a description of changes (with reason)
 - [x] If you've fixed a bug or added code that should be tested, add tests!
 - [ ] If necessary, also make a PR on the [nf-core/hlatyping branch on the nf-core/test-datasets repo]( )
 - [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
 - [ ] Make sure your code lints (`nf-core lint .`).
 - [ ] Documentation in `docs` is updated
 - [ ] `CHANGELOG.md` is updated
 - [ ] `README.md` is updated

**Learn more about contributing:** https://github.com/nf-core/hlatyping/tree/master/.github/CONTRIBUTING.md

## Description 

This PR address the issue #68. 

The main problem was the index was not properly declared in the `remap_to_hla` process inputs declared. 

I guess this was not done because the input it's not just a single index file, but multiple ones. To make things worse the `yara_mapper` uses the ugly approach to take as input params not a fake path name and using it to resolve all the dependant files e.g. `hla_reference_dna.rid.limits`, `hla_reference_dna.sa.ind`, etc. 

I've fixed introducing the following params:

```
  base_index_type = 'dna'
  base_index_path = "$baseDir/data/indices/yara" 
  base_index_name = "hla_reference_$params.base_index_type"
``  


This is also related to https #76 since the PR removes the `index` params .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11bd58053280`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.