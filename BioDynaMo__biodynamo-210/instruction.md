# Issue

**Title:** Suggest change API for Normalize()

## Description

The current API allows the following:

```cpp
INFO: Created simulation object 'simulation' with UniqueName='simulation'.
root [1] Double3 x{1,2,3};
root [2] Double3 normalized = x.Normalize();
root [3] normalized
(bdm::Double3 &) { 0.26726124, 0.53452248, 0.80178373 }
root [4] x
(bdm::Double3 &) { 0.26726124, 0.53452248, 0.80178373 }
root [5] &normalized
(bdm::Double3 *) 0x100879938
root [6] &x
(bdm::Double3 *) 0x100879700
```

After line 2, one might expect a normalized `MathArray` `normalized` and an unnormalized `MathArray` `x`. At least one user was getting strange results in his simulation because he did not expect this kind of behavior. Basically, it allows for a normalization followed by a copy operation. But I don't see a strong argument for having it like this. It would make more sense to copy first, and normalize the copy leaving the original unchanged. Because otherwise, one ends up with two equal objects in memory as can be seen in `root [3,4]`.  

This PR changes `MathArray& MathArray::Normalize()` to `void MathArray::Normalize()` and additionally introduces a member `MathArray MathArray::GetNotmalizedArray() const` (plus test).

With this structure, I believe one could avoid issues arising from unintentionally normalizing the original object as for instance in line `root [2]`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ee51cdb5f77`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.