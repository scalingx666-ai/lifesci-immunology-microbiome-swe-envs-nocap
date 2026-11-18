# Issue

**Title:** arda 2.7.2 — second `--two-pass` crash fix; `_subset_db` behaviour pinned

## Description

## Fixed — a second `--two-pass` crash, on alignment rows with no score

2.7.1 dropped rows with a blank query id; the amplicon run then died at the next site instead:

```
TypeError: float() argument must be a string or a real number, not 'NoneType'
```

`bits` is cast with `strict=False`, so an unparseable score becomes null rather than raising at
parse time, and that null reached `float(row["bits"])` in the J+C contest. Same malformed row,
second crash site. Both are now filtered in one place, and both route the affected read to the
full-reference rescue — the guarantee `--two-pass` is built on.

**With both fixes, `--two-pass` completes on amplicon for the first time.** 1 M pairs, `map` stage:

| sample | wall | vs one-pass | lost | v_gene | junction_aa | rescued |
|---|---|---|---|---|---|---|
| SRR5233635 TRA | 455.33 s | **1.77×** | **10** | .9994 | **.9995** | 157,824 (16 %) |
| SRR5233641 TRB | 479.35 s | **1.73×** | **16** | .9817 | **.9984** | 299,860 (30 %) |

It is the only amplicon lever measured that preserves calls: `--adaptive` is 3.15× but moves 34 %
of V-gene calls in that regime, and a one-allele-per-gene reference costs 42 % of allele-level V
calls on TR data by construction.

⚠ **Defensive fixes, not a root cause.** 16–30 % of reads still fall through to rescue, which is
most of what `--two-pass` gives back in speed, and the malformed rows point at the same origin.
The sub-DB construction still needs an audit.

## Fixed — a stale claim about `createsubdb`, and code written on top of it

`_subset_db`'s docstring said `createsubdb` does not write a `.lookup` for the destination. **It
does** — verified against mmseqs 18-8cc5c, which also copies it *whole* rather than subsetting it.
Writing that file by hand on the stale assumption (an attempt to explain the blank query names)
overwrote mmseqs' own and broke the rescue path with "490 ids absent from lookup". Reverted; the
docstring now records verified behaviour, and states plainly that the blank query names have
another, still-unknown cause.

## New tests

`tests/unit/test_subset_db.py` — four invariants of the hand-built query sub-DB the two-pass fast
path aligns against. Each has shipped broken at least once, and **every one fails silently**: a
malformed sub-DB does not raise, it makes reads fall through to rescue or produces alignment rows
attributable to no read.

* `createsubdb` writes `.lookup`, and copies it whole (surplus entries are expected, not a bug)
* the `_h` pair is created — without it `convertalis` emits numeric keys, not names
* source keys are preserved, so the caller's name→key mapping stays valid afterwards
* an unknown id raises rather than being dropped — this sits on the no-read-lost path

## Verification

`pytest tests/unit tests/realworld` **491 passed** · `ruff check src/` clean · docs build under `-W`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4198a291e24b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.