# Issue

**Title:** Fixed ivar_variants_to_vcf.py exception

## Description

<!--
# nf-core/viralrecon pull request

Many thanks for contributing to nf-core/viralrecon!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/viralrecon/tree/master/.github/CONTRIBUTING.md)
-->

## PR checklist

- [ ]  The ivar_variants_to_vcf.py would occasionally throw an unhandled StopIteration exception when handling the last few lines of the VCF and codons were being merged. The proper changes to the code have been made, by adding the proper data structure. This created a logging issue were incorrect counts for each mutation type were sometimes incorrectly handled. This problem was altered by converting the q_pos deque structure to hold tuples instead of lists. The output of the files was also slightly tidied through the use of format strings. 

The traceback of the StopIteration exception is below.
```
Traceback (most recent call last):
  File "/mwells/viralrecon/bin/ivar_variants_to_vcf.py", line 577, in <module>
    sys.exit(main())
  File "mwells/viralrecon/bin/ivar_variants_to_vcf.py", line 552, in main
    fe_codon_ref = variants[next(iter(variants))]["ref_codon"]
StopIteration
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f07405f76478`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.