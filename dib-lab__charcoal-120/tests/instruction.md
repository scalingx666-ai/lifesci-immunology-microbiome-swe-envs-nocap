# Issue

**Title:** Add support for protein searches & decontamination

## Description

viz #119 

This is running to completion on the demo data!! A few notes --

To run it, I think you'll need to install current sourmash master, because of some LCA database features that are needed. This also means running without conda. I'm using:
```
charcoal run demo/demo.prot.conf --no-use-conda -j 4 -p -k
```

You'll also need the file `/home/ctbrown/charcoal/demo/demo.prot-matches.sig.gz` in your own demo subdir. It's too big for me to add it to this PR until I'm sure all this stuff works!

The various fractions (for f_ident, f_major, etc.) in just_taxonomy.py need to be tuned... For now, I just made them 10x lower.

---

other thoughts:

- XXX if we're serious about this, should probably plan on running prokka to extract proteins. or maybe six-frame translation of DNA is better, b/c could catch fragmented genes w/o reducing specificity?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af435fc6aef3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.