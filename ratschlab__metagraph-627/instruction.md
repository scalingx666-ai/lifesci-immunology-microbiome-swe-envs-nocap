# Issue

**Title:** query: compact RLE encoding for k-mer presence bitmasks (signature mode)

## Description

## Summary

- Replaces the raw binary bitmask string in `--query-mode signature` output with a compact run-length encoding (RLE)
- `--verbose-output` retains the full binary string (no behaviour change for existing users who pass that flag)

## New format

```
x<N>o<N>...
```

- `x<N>` — run of **N present** k-mers
- `o<N>` — run of **N absent** k-mers
- Runs alternate; trailing absent-runs are **always included** so the total k-mer count equals the sum of all run lengths

### Examples

| Binary mask    | Encoded         |
|----------------|-----------------|
| `11100110`     | `x3o2x2o1`      |
| `00011111`     | `o3x5`          |
| `10000001`     | `x1o6x1`        |
| `00000000`     | `o8`            |
| `11111111`     | `x8`            |
| `10101010`     | `x1o1x1o1x1o1x1o1` |

### TSV output (text mode)

```
<seq_id>\t<seq_name>\t<label>:<kmer_count>:<mask>:<score>...
```

Example:
```
0	query1	<seq2>:13:x13:17	<seq1>:10:x4o1x3o1x3o1:15
```

### JSON output

```json
{
  "presence_mask": "x4o1x3o1x3o1",
  "score": 15
}
```

### Verbose output (unchanged)

Pass `--verbose-output` to get the original binary string:
```
0	query1	<seq2>:13:1111111111111:17
```

## Decoder (for client updates)

```python
import re

def decode_presence_mask(s: str) -> list[bool]:
    return [
        bit == 'x'
        for token in re.findall(r'[xo]\d+', s)
        for bit in token[0] * int(token[1:])
    ]
```

## Changes

- `src/cli/query.cpp` — `encode_presence_mask()` helper; `to_json`/`to_string` use it by default
- `src/cli/config/config.cpp` — updated `--query-mode signature` and `--verbose-output` help text
- `docs/source/quick_start.rst` — new "Query k-mer presence masks" section
- `tests/cli/test_query.cpp` — 7 unit tests
- `integration_tests/test_query.py` — 15 integration tests (default RLE + verbose binary)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d4a7de34af7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.