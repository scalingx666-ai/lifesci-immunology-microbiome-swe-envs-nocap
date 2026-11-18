# Issue

**Title:** Clamp PSSM scores before casting to char

## Description

## Problem

`PSSMCalculator::computeLogPSSM` cast each rounded score to `char` before clamping it to [-128, 127]:

```cpp
pssmVal = static_cast<char>((pssmVal < 0.0) ? pssmVal - 0.5 : pssmVal + 0.5);
float truncPssmVal =  std::min(pssmVal, 127.0f);
truncPssmVal       =  std::max(-128.0f, truncPssmVal);
pssm[idx] = truncPssmVal;
```

- Out-of-range values wrapped before the clamp could act, so the clamp did nothing.
- Converting an out-of-range float to `char` is also undefined behavior.

In practice the low byte is kept, which gives:

| Unclamped score | Before | After |
|---|---|---|
| -1024 (probability 0: `flog2` returns -128, × bitFactor 8) | 0 | -128 |
| -200 | 56 | -128 |
| 127.5 / 128 | -128 | 127 |
| 300 | 44 | 127 |

As a result, impossible residues scored as neutral, and very unlikely residues could get positive scores.

## Fix

Round as a float, clamp, then cast. The rounding is unchanged (half away from zero).

## Impact

- Scores that were already within [-128, 127] are unchanged.
- Out-of-range scores now stop at -128 or 127 instead of wrapping.
- Both callers (`computePSSMFromMSA` and `sequence2profile`) get the fix. No interface or format changes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fcf516aba34b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.