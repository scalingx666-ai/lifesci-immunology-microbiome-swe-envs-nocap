# Issue

**Title:** Update rosella to v0.5.0

## Description

Update includes:
- rosella v0.5.0: better run speed for both binning and refining
- checkm2 yaml update. Conda was somehow choosing incorrect versions of numpy and pandas
- add CITATION.cff for repo citing

Testing:
- [x] run rosella
- [x] test checkm2 conda creation
- run rosella refine on:
- [x] rosella output
- [x] semibin output
- [x] metabat2 output

## Main sticking points:
### Are unchanged bins being copied correctly and is checkm data preserved?
I think they are, I've tested on small samples but a large run would not hurt

### Ensure checkm2 yaml change was not just an issue with my conda setup
I'm pretty sure it wasn't, but it is weird that it just started installed incorrect versions when previously it has been fine. Should double check on another machine if possible

### Large sample check
I've not run on a large sample just the CAMI I low complexity test

### Are results improved?
I think the MAG recovery results should be improved from this update, but it would good to see some benchmarks

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `145775596837`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.