# Issue

**Title:** Speed up construction of universe from IntervalSets

## Description

`set_cover.approx_multiuniverse()` constructs the universes by taking
the union over all input sets. When `use_intervalsets` is True,
this was previously slow. (`use_intervalsets` is True for most runs because
[`set_cover_filter` sets it to True](https://github.com/broadinstitute/catch/blob/745499f9e2c3d2c88fc6da45b0e10c6c58a6de22/catch/filter/set_cover_filter.py#L735).) It worked by creating an empty
IntervalSet, and then repeatedly taking the union of the universe's
IntervalSet with another input set (also represented as an IntervalSet).
In the worst-case, taking the union takes O(_n_) time where _n_ is the
current size of the universe. As a result, constructing the universe
took, in the worst-case, O(_n_^2) time. For particularly long genomes,
where _n_ is large, this could take hours in practice.

This fix instead initializes each universe by simply constructing
a list of the input intervals for it, and then initializing an IntervalSet
from the list. Initializing the IntervalSet already merges overlapping
intervals (effectively taking the union of all of them) in O(_N_ log _N_)
time, where _N_ is the number of input intervals. Since the input sets
are constructed from the universe, _N_ is O(_n_), where _n_ is defined above.
So, now, constructing the universe takes, in the worst-case, O(_n_ log _n_)
time. In practice, this seems to provide a noticeable speed up as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `745499f9e2c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.