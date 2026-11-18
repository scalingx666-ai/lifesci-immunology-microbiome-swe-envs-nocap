# Issue

**Title:** Fix importTaxpasta

## Description

using taxpasta via nf-core/taxprofiler v1.1.8 and tried to use importTaxpasta to get a tse. I got an error like `type field has unsupported value` (see [here](https://github.com/joey711/biomformat/blob/0de05b1e78ea6ed42e079e07ccb13cecfd9eba6a/R/validity-methods.R#L66)). after some digging around i see it looks like the taxpasta biom leaves this field empty.

this pr represents a proposal to have this type default to 'OTU table'. it also proposes making `addHierarchyTree` optional when importing taxpasta data. my particular use case doesnt require it, and its a bit time consuming. 

i also notice addHierarchyTree seems to not handle fully unclassified entities well. Im considering improving that situation out of scope for this PR unless someone objects, and am happy to file an issue if i dont find one once i have more details. but its also influenced my desire to make it optional in this context, so thought id mention it here.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `552a9521c19d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.