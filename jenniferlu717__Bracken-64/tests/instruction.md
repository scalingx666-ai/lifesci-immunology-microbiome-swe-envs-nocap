# Issue

**Title:** search for build scripts in path if not where expected

## Description

This PR should hopefully  .  

If the directory obtained on this line https://github.com/jenniferlu717/Bracken/blob/80cc434d97c2a61461f7b6c9cde894f66b94b3cc/bracken-build#L144 does not contain the `src` directory with the accessory scripts, then `bracken-build` fails.  
I came across this because I had copied `bracken` and `bracken-build` to `/usr/local/bin/` and as such there is no scripts directory under the binaries for these. In this case I actually had `kmer2read_distr` in my `$PATH` but the build script couldn't find it as it was only searching near the `bracken-build` binary which was in `/usr/local/bin/`.   

As such, this PR will search for `kmer2read_distr` and `generate_kmer_distribution.py` in the `$PATH` and if they are there it will use them.  

I'm not sure if you have some tests to make sure this works as there is no tests in the repository? You may want to merge into a `dev` branch or something before pushing to `master`?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80cc434d97c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.