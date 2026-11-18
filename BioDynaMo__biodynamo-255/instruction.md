# Issue

**Title:** Add left-multiplication to MathArray

## Description

Previously:

```cpp
root [1] Double3 x {1,2,3};
root [2] x * 4.0
(bdm::MathArray) { 4.0000000, 8.0000000, 12.000000 }
root [3] 4.0 * x
ROOT_prompt_3:1:5: error: invalid operands to binary expression ('double' and 'bdm::Double3' (aka 'MathArray<double, 3>'))
4.0 * x
~~~ ^ ~
/Users/tobias/tmp/biodynamo/build/third_party/root/include/TH1.h:483:6: note: candidate function not viable: no known conversion from 'bdm::Double3' (aka 'MathArray<double, 3>') to 'const TH1C' for 2nd argument
TH1C operator*(Double_t c1, const TH1C &h1);
     ^
[... lengthy output ...]
```

Now:
```cpp
root [1] Double3 x {1,2,3};
root [2] x * 4.0
(bdm::MathArray) { 4.0000000, 8.0000000, 12.000000 }
root [3] 4.0 * x
(bdm::MathArray<double, 3UL>) { 4.0000000, 8.0000000, 12.000000 }
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e1d0d94bcc4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.