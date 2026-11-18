# Issue

**Title:** keep '$' characters in TEXT keyword values

## Description

`__parse_pairs` runs `text[1:-1].replace('$', '')` on the whole TEXT segment before splitting it. That removes `$` from values as well as keywords:

```python
from flowio import FlowData
FlowData._FlowData__parse_pairs('/$FIL/run$7.fcs/$COM/cost $50/')
# {'fil': 'run7.fcs', 'com': 'cost 50'}
```

Keyword values are free text, encoded in UTF-8 (FCS 3.1 section 3.2.8), so `$` is legitimate data there, for example in `$FIL`, `$SRC`, `$COM` or `$PnS`. The value is also lost when the file goes through `write_fcs`.

Fix: strip `$` from keywords only. The splitting is unchanged, and keyword names stay exactly as before (`$P1N` -> `p1n`, `BD$NPAR` -> `bdnpar`), so no lookups change.

Tests: a new `DollarSignTestCase` with one parser-level test and one that reads an in-memory FCS 3.1 file with `$FIL/run$7.fcs/`. Both fail on develop and pass with the change. Full suite on develop: 48 passed, 1 failed before; 50 passed, 1 failed after (the same `test_as_array_with_preprocessing` failure, #44).

I also read 88 FCS files (the repo test files, the FlowKit and fcsparser test data, and synthetic variants) with and without the change. TEXT and event counts are identical for all of them except the one synthetic file that has a `$` in a value.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38a18bc8be37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.