# Issue

**Title:** Place the junction by arithmetic, not by alignment

## Description

## What

`arda.annotate.project` places the AIRR `junction` from segment coordinates alone:

```
offset = (anchor_nt + 1) - tstart
pos    = qstart + offset                    # forward hit
pos    = (qlen - qstart + 1) + offset       # reverse-complement hit
```

The 15,414-scaffold V×J reference exists to locate two codons — Cys104 and the [FW]118 that opens FR4. The segment pass already returns `(target, tstart, qstart)` per read per side, and `cdr3_anchors.tsv` already records `anchor_nt`. `refbuild.segments` writes the V target as `scaffold[:v_sequence_end]` and the J target as `scaffold[j_sequence_start - 1 : vj_end]`, so target coordinates *are* germline coordinates and the anchor is two integer adds away.

## Measured

**54,740 / 54,756 = .99971 byte-exact junctions** against IgBLAST across a TRA amplicon, a TRB amplicon and a bulk library, at no cost beyond the segment pass that already runs.

On the 301-read `realworld` human fixture: 227/228 byte-identical to the scaffold path, **21 reads gained a junction the scaffold did not produce**, 7 refused on the frame check. The single disagreement has a *scaffold* junction of 44 nt — not a multiple of 3 — which the projection refuses.

## Scope, set by yield rather than accuracy

**87.0 % of hit TRA-amplicon reads and 77.3 % of TRB carry both anchors, against 7.2 % of bulk reads** (bulk is 53.0 % `V_only`, 31.4 % `C_only`). Bulk reads mostly do not span a junction at all, so no anchor primitive buys a junction there. This is an amplicon lever.

## Not wired into the output path yet, deliberately

It yields `junction` and its coordinates. It does **not** yield `v_identity`, `sequence_alignment`, `germline_alignment`, the per-segment CIGARs or the `mmseqs2_*` block, all of which `annotate.transfer` derives from the alignment's `qaln`/`taln`; `_align_implied` also decides the allele. Whether removing junction placement from the critical path recovers wall time is the next measurement, and shipping it into the output first would make a disagreement read as a regression instead of a measurement.

`ARDA_PROJECT_DUMP` writes the projection beside the scaffold answer so that comparison can be made at scale. Off by default.

## Refuses rather than degrades

Six conditions send the read back to the aligner: missing or non-`ok` anchor, `segmap`'s two-diagonal indel signature, V and J on opposite strands, order violation, projection off the read, and a junction length that is not a multiple of 3. A well-formed junction that is wrong is the worst output this codebase produces — the reference-geometry bug shipped junctions that started `C`, ended `[FW]`, passed `--complete-only` and were short by exactly the allele's truncation.

## Why not a motif scan

Bitap at a usable operating point measured **1,381–3,586 ms/100k reads at 8 threads against 180.9 ms** for the segment pass it would sit beside; one exact 21 nt bitap pass already costs more per thread than arda's whole 924-target index. Two structural reasons: the mismatch budget is *shared* between probe-set cover and SHM (TRA V needs 94 patterns at k=0 and still 40 at k=8), and a seed index gets ~103 clean 12-mers per V at 91.77 % identity while a single anchor window gets one shot.

⛔ And a motif check is not equivalent to reading `anchor_nt`: **`TRAJ35*01`'s anchor decodes Cys (TGC), not [FW]** — it is `status = ok` and a functional IMGT `F` gene. A `[FW]GXG` check deletes it silently (33/33 amplicon reads lost).

## Tests

11 new, including one that runs the arithmetic against the **shipped reference** and asserts the anchor offsets decode to real Cys / Phe / Trp codons — so a reference rebuild that moves the coordinate system is caught rather than silently mis-placing every junction. Three coordinate systems disagree about their origin here (`tstart` 1-based on the forward target, `anchor_nt` 0-based in the germline, minus-strand `qstart` in forward coordinates indexing a reverse-complemented sequence) and each is pinned separately.

Full suite green (536), `ruff check src/` clean.

## Open

Three kill risks, each with a bar, measuring now as job 1424827: the AIRR alignment block may make the saving zero (≥1.25× wall with zero clonotype change); **TRD sits at 43/51 = 0.843** against .99971 pooled (≥0.99 at n≥2,000/locus or refuse the locus); and `split` refusal was measured on TR amplicons with no SHM against a real IGH indel rate of 8.00 % below 90 % V identity (<10 % refusal).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d23830da4f36`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.