# Issue

**Title:** pack_reference.sh: reject an empty reference file, not just a missing one

## Description

## Problem

`scripts/pack_reference.sh` validates that each required reference file is **present** in the asset (`grep -q`) but not that it is **non-empty**. A `build-db` run without IgBLAST emits 0-byte `alleles.*`/`markup.*`, which pass the presence check, ship in `arda-reference-vdj.tar.gz`, and then crash **every fresh `pip install`** at load time:

```
polars.exceptions.NoDataError: empty CSV
  at arda/annotate/reference.py:load_reference
```

**v2.5.7 shipped exactly this.** The published asset was re-uploaded good ~3 h after the release (verified: it is now byte-identical to the committed reference, all 5 organisms, 345 J+C scaffolds), but nothing in CI would have caught the empty asset — the guard just wasn't there.

## Fix

A 1 KB size floor per required file, measured by extracting the *packed* member to stdout so it reflects what actually ships:

```bash
sz=$(tar -xzf "$OUT" -O "vdj/$org/$f" | wc -c)
[ "$sz" -gt 1000 ] || { echo "ERROR: vdj/$org/$f is empty ($sz B) ..."; exit 1; }
```

- **Portable** across bsdtar (macOS) and GNU tar (CI) — tested on both paths.
- **Can't false-trip**: smallest real file is `rat/cdr3_anchors.tsv` at ~24 KB, a 24× margin under the 1 KB floor.
- **Runs in the release path**: `pack_reference.sh` executes in the `reference-asset` CI job *before* `gh release upload`, so an empty reference now fails the release instead of shipping.

## Test

- Positive: packing the real committed reference reaches `OK`, exit 0 (53 members, 2.8 MB).
- Negative: emptying one required file → `ERROR: vdj/human/markup.aa.tsv is empty (0 B)` and non-zero exit before the `OK` summary.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18addc9bcd17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.