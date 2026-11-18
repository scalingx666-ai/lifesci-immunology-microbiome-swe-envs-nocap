# Issue

**Title:** IG V-gene accuracy is read coverage, not SHM — plus `--d-prior`, a re-priced `--adaptive`, and the coverage floor in the docs

## Description

> ℹ️ Contains the commit from the now-closed #124 (`6266c59`, the round-29 IG measurement — the Cys104 constant holds on IG: +1,027 correct junctions, 744 clonotypes, and that part stands). `231cd80` withdraws the `v_gene` headline it raised.

You asked for the `v_gene` measurement on `SRR5233637-40`. It overturns what  put at the top of the roadmap one round ago.

Full record: `~/vcs/projects/2026-arda-benchmark/results/round30`.

## ⛔ SHM is not the driver — the gradient is non-monotonic

IgBLAST's own `v_identity` is the SHM load on the read. 98,639 IGH truth reads:

| `v_identity` (%) | reads | `v_gene` recall |
|---|---:|---:|
| ≥ 99 (unmutated) | 6,196 | .9425 |
| 97 – 99 | 13,648 | **.7518** ← worst |
| 95 – 97 | 18,470 | .8685 |
| 92 – 95 | 26,676 | **.9697** ← best |
| 88 – 92 | 19,347 | .9624 |
| < 88 (heavy SHM) | 14,302 | .9046 |

The worst bin is nearly unmutated, the best is moderately mutated.

## What does order it: how much V the read covers

| V germline span | reads | % | recall |
|---|---:|---:|---:|
| < 60 nt | 5,802 | 5.9 % | **.1170** |
| 60 – 90 | 978 | 1.0 % | .6748 |
| 90 – 120 | 4,224 | 4.3 % | .5727 |
| 120 – 160 | 1,845 | 1.9 % | .9507 |
| 160 – 200 | 33,903 | 34.4 % | .9647 |
| **≥ 200** | 51,887 | 52.6 % | **.9896** |

**At ≥ 200 nt arda scores .9896 — the TRA amplicon's .9867.** 5.9 % of reads produce ~56 % of every V miss.

The mechanism is visible read by read: `IGHV1-69 → IGHV1-18` is **4,745 of ~9,080 misses**, and on those reads IgBLAST aligns germline **242–296 — 55 nt of the V's 3' end**. A 5'RACE read runs C → J → V, so the bases separating one IGHV from another are not in the read. IgBLAST lists **1.64 V genes per read itself**: a different tie-break on the same missing evidence, not a better one. `genotype.md` already measured this on TCR — TRAV needs ~175 nt from the 3' end, TRBV ~150.

**Position beats length.** A short *5'* alignment identifies the gene; a short *3'* one does not, because IGHV diverges in FR1/CDR1/CDR2 and is conserved in FR3 near Cys104. 5,714 of 5,802 short 5'RACE alignments start at germline 200–249; in bulk only 216 do — same "short" bin, **.1170 vs .8472**.

## Replicated on libraries arda did not select

`SRR5233639` / `SRR5233640`, bulk melanoma RNA-seq, 660 k R1 reads each, `arda igblast` truth.

| locus | 639 | 640 | top span bin |
|---|---:|---:|---:|
| IGH | .9331 | .9373 | .9661 / .9689 |
| IGK | .9828 | .9802 | .9879 / .9897 |
| IGL | .9494 | .9470 | .9938 / .9903 |

Monotonic in span for every locus and both samples, agreeing within 0.5 points. 100 nt reads cannot reach the 120+ bins — which is the whole point.

✅ **Corrected headline: arda's IG V-gene accuracy is .93–.98 on bulk and .9896 when the read carries ≥ 200 nt of V. There is no 9-point IG defect.**

## ⛔ The obvious fix was measured and rejected

A V-call evidence gate — the same discipline `transfer.py` already applies to `j_call` — dropping a call that starts at germline ≥ 150 and spans < 60 nt:

| library | precision before | after | recall cost |
|---|---:|---:|---:|
| IGH 5'RACE | .92585 | **.97693** | −0.69 pt |
| IGH bulk | .93467 | .93942 | **−3.24 pt** |
| IGK bulk | .98301 | .98304 | **−6.22 pt** |
| IGL bulk | .95000 | .95002 | **−2.39 pt** |

A 7.6 : 1 win on one library/locus and a clear loss on three. A shipped constant would be wrong more often than right, which is why this repo ships none.

**Item 6 now asks for a bit-score margin on the V *tie list* instead** — arda already emits one (61,638 reads get 1 gene, 10,266 get 2, 24,836 get 3), and the misses are reads whose list does not contain the truth gene *at all*. Admitting the ambiguity the read really has, rather than refusing the call, and it reuses `arda resolve-ties`.

## Also recorded

`IGHV3-52` and `IGHV3-71` have **0 scaffolds** in arda — `load_functional_alleles` excludes IMGT ORF/pseudogenes by design while IgBLAST's DB includes them. 476 reads. A policy question (scaffold set vs call vocabulary are different decisions), flagged for your call, not changed.

⚠ `SRR5233637`/`SRR5233638` (patient SPX8151) carry ~1,900 IGH reads per 660 k against SPX6730's ~7,000; their truth was still building. They are a second-*patient* check, not a second geometry, and the conclusion rests on 5'RACE vs bulk.

Docs only; no code changes. `ruff check src/` clean, docs build with zero warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---

# A rule for the reference gene vocabulary

arda ships **82 of the 121 human IGHV genes** IgBLAST's germline DB carries — `load_functional_alleles` excludes IMGT ORFs and pseudogenes by design. A read from an excluded gene isn't dropped; it's called as the nearest gene that *is* present. A confusion table alone can't say whether that's a defect or a policy, so `CLAUDE.md` now carries three checks to run before any gene joins or leaves, and `SOURCES.md` records what they returned.

**1. Literature — is the gene attested in real repertoires?** Retrieved through the `citations` skill, never from memory. IGHV3-53/3-66 are a *public antibody* pair repeatedly induced by SARS-CoV-2 infection and vaccination, explicitly contrasted with IGHV1-69 — Kuwata T, Kaku Y, Biswas S, et al., *EBioMedicine* 2024;110:105439, PMID [39488016](https://pubmed.ncbi.nlm.nih.gov/39488016/), doi:[10.1016/j.ebiom.2024.105439](https://doi.org/10.1016/j.ebiom.2024.105439).

**2. Expression — is the locus transcribed, in the right tissue?** `IGHV3-71` is an **IG V pseudogene** (`ENSG00000254056`, HGNC:5621) — and GTEx shows it transcribed wherever B cells are: spleen **3.45 TPM**, minor salivary gland 2.39, transverse colon 1.33, terminal ileum 1.30, EBV-transformed lymphocytes 0.378, essentially zero in ~35 of 54 tissues. ⚠ "Pseudogene" is a claim about the protein, not about whether reads exist.

**3. The tied-hit test — would admitting it add information, or only ambiguity?**

| pair | 3' identity | reading |
|---|---:|---|
| `IGHV3-23` / `IGHV3-23D` | **1.0000** | a true tie — no read can ever separate them |
| `IGHV3-30` / `IGHV3-30-3` | **1.0000** | a true tie |
| `IGHV3-53` / `IGHV3-66` | 0.9898 | near-tie; a two-gene call is the honest output |
| `IGHV3-71` / `IGHV3-49` | **0.9172** | separable — mis-assigned today, not tied |
| `IGHV3-52` / `IGHV3-7` | **0.9088** | separable — same |
| `IGHV1-69` / `IGHV1-18` | 0.9054 | separable, so that confusion is **not** homology |

**≥ ~0.99 buys a longer tie list and nothing else; ≤ ~0.95 means reads are being actively mis-assigned.** Both absent genes fall in the second band.

That last row is also the negative control the coverage argument needed: `IGHV1-69`/`IGHV1-18` at 0.9054 are *separable*, so the 4,745-read confusion isn't homology — which is what leaves the 55 nt read span as the explanation.

⚠ The **scaffold set** and the **call vocabulary** stay separate decisions: scaffold ids are positional, so adding one renumbers the locus and invalidates every precompiled index. Nothing is changed here — both need your call.

`SOURCES.md` carries the commands that re-derive both gene sets (verified: 121 and 82).

---

## Added since the review above (`8102f00`)

Three ROADMAP items, none of which needed a new measurement — all three were already priced and
were waiting on someone to wire or write them down.

### `arda markup --d-prior PATH` — ROADMAP item 7

`arda scenarios` fits exactly the table `arda.dpost` reads, and `docs/scenarios.rst` calls its
output a drop-in for `database/vdj/<org>/d_prior.tsv`. It was — **by format**. `load_d_prior` was
`@lru_cache`d on the organism alone and read one fixed path, so the only way to *use* a fitted
table was to overwrite a file inside the installed database: a change that silently alters every
later run on the machine and leaves no record it happened.

`load_d_prior(organism, path)` and `posterior_d(..., prior_path=)` now take one; the CLI flag
implies `--d-posterior`, because a parameter accepted while doing nothing is this project's
recurring failure. This is what makes **item 8** approachable — 11 of the 13 shipped
`(organism, D-locus)` pairs have no prior because OLGA has no model for them, and a table fitted
from a real cohort can now be tried against them without being installed first.

⚠ The shipped table is *allowed* to be missing (that is what `None` means); a path the caller
typed is a request, so a `--d-prior` that is not there **raises** rather than scoring on an empty
prior. Six new tests, including one that gives rhesus TRB — which ships none — a posterior from a
hand-made table and then asserts the shipped human answer is unchanged.

### `--adaptive` re-priced, two stale read-path claims deleted — ROADMAP item 5

The help text and the comment at `_ADAPTIVE_TRIGGER` quoted **"3 of 453 reads"** from a fixture.
Re-measured at **79× that scale** (660,000 real bulk pairs, benchmark round 27), the fixture
*understated* it:

| | fixture (453 reads) | 660,000 real bulk pairs |
|---|---|---|
| wall | — | **1.84×** (16.34 → 8.90 s) |
| CPU | — | **3.04×** (198.20 → 65.13 s) |
| peak RSS | — | 1.34× (1,033 → 771 MB) |
| rows whose `junction` moved | 3 of 453 | **93 of 35,795** |
| direction | — | **89 to empty, 4 the other way** (net −85 of 3,856) |
| above the 90-bit trigger | 2 of 3 | **91 of 93** |

So the score-only trigger is **uncalibratable**, not untuned. Default unchanged: off.

With it, `rnaseq/map.py`'s *"reading is 65 % of a bulk run"* — true *before* the dnaio port that
comment motivated, and made false by it. Reading is **0.73 s of map's 16.19 s = 4.5 %**; mmseqs +
transfer + format is 95.5 %. The `--chunk-size` sweep beside it existed to overlap the reader with
the search, so with nothing left to overlap, **1 chunk vs 4 is 16.48 s vs 16.34 s**, byte-identical.

### The coverage floor, written where a user will find it

`docs/usage.rst` gains *"What an IG V call means when the read is short"* — both span tables, why
position beats length, why SHM does not order it, and why no threshold ships. Summarised in
`README.md` next to the existing allele-level note, and one line in `skills/arda/SKILL.md`.

### The second-patient check is finished — SPX8151

`SRR5233637` / `SRR5233638`. A second **patient**, not a second geometry, and it replicates the
one thing it was asked to: `v_gene` recall is monotonic in V germline span on **all six arms**.

| locus | 637 all | 638 all | < 60 nt | 60–90 | 90–120 |
|---|---:|---:|---:|---:|---:|
| IGH | .9103 | .9058 | .6887 / .6763 | .8238 / .8538 | **.9649 / .9546** |
| IGK | .9770 | .9782 | .9137 / .9013 | .9684 / .9804 | **.9890 / .9890** |
| IGL | .8512 | .8793 | .4286 / .4490 | .5568 / .6449 | **.9588 / .9822** |

1,317–1,558 truth reads per locus per sample at `v_score ≥ 70`; the two samples agree within 0.5
points on IGH and IGK.

**And it names where a wider tie list cannot be the fix.** `truth genes/read` — how many distinct V
genes IgBLAST itself listed — is **1.49–1.71 on IGK** (the judge could not separate them either, so
a longer list is exactly right) but **1.02–1.09 on IGL**, where IgBLAST resolves a single gene and
arda still misses 55 % of the `< 60 nt` bin. Those are tie-*break* errors on evidence that exists.

---

## Round 31 — the same molecules read from both ends (`a596258`, `eb43043`)

Two human IGH libraries pulled off aldan3 through the **ngsik** registry: a **multiplex V-primer
amplicon** (reads start at FR1) and a **5'RACE** control, both MiSeq, both 251 nt, both read from
*both* ends. Full record: `~/vcs/projects/2026-arda-benchmark/results/round31`.

Round 30 argued "position beats length" across libraries, patients and protocols. The multiplex
library's two mates are the **same molecules** — same patient, run, instrument, read length, arda
version and truth builder:

| arm | covers | median V span | `v_gene` recall | precision |
|---|---|---:|---:|---:|
| multiplex **R1** | C → J → V 3' end | 58 nt | **.0265** | .9786 |
| multiplex **R2** | FR1 → 3' | 247 nt | **.9894** | .9967 |
| 5'RACE **R1** | C → J → V 3' end | 146 nt | **.9645** | .9728 |
| 5'RACE **R2** | 5' end of V | 100 nt | **.8895** | .9097 |

✅ **The bin that is the same object in all four arms agrees to three places.** `v_gene` recall on
reads carrying ≥ 200 nt of V germline: **.9891 / .9935 / .9923 / .9930**, against round 30's .9896
on a third library and the TRA amplicon's .9867.

⛔ And **"5'RACE" is not a risk factor** — the same protocol scores .1170 on a short read and
**.9645** at 251 nt. The 5'RACE arm also isolates position from length *inside one protocol*: at a
near-constant span (137–154 nt), recall is **.9763** starting at germline 100 and **.7801**
starting at 200.

### A silent usage trap, now in `CLAUDE.md`

Mapping **one mate** of a C-anchored amplicon returns `j_call` + `c_call` on 98 % of reads,
`v_call` on **1.9 %** and `junction` on **40 of 49,036 rows** — at exit 0, "98.07 % mapped",
correct locus, J and isotype. The reference holds 15,069 V·J scaffolds of which **0 carry a
constant region** and 345 J+C scaffolds with no V, so a read reaching ~80 nt into C scores
**244 bits against 241**. The partition is exact: 48,156 / 891 / **0** / **0**. Trimming only the
constant region moves recall **.0265 → .8775** and junctions **40 → 40,005**; the amplicon preset
gives the same 1.9 %.

Same command on the 5'RACE library, whose C primer sits close to the J: `v_call` **95.9 %**,
`c_call` 4.1 %, `junction` **92.7 %**. So the cause is the C tail, not the protocol.

⚠ Not a defect, and I changed no arbitration: `mapper.py`'s J→C contest is working as designed and
its comment records what broke last time it was forced (3 of 453 reads gained a fabricated
`junction_aa` and lost their `c_call`). `arda amplicon --r1 --r2` handles the library — 24,655
contigs, 100 % complete, 8,519 clonotypes.

### ROADMAP item 4 is answered for IGH, opposite to TCR

100,000 pairs, 3 reps, medians, **idle machine**:

| arm | wall (s) | CPU (s) | clonotypes |
|---|---:|---:|---:|
| `arda amplicon` | 255.64 | 1,635.91 | **13,040** |
| `--no-assemble` | **169.07** | **1,212.22** | 108 |

Assembly costs 1.51× wall and 1.35× CPU and buys **12,932 of 13,040 clonotypes (99.2 %)**, against
0.025 % on TRA and 0.013 % on TRB. Almost noiseless — 13,040 and 108 exactly, every rep — because
neither mate spans V into J. **`--no-assemble` must never become a preset.** No default changed.

⚠ The first attempt at that A/B was started beside two IgBLAST truth builds (load average 173) and
was killed rather than reported; medians do not rescue a contended timing run, they average the
contention.

⚠ **Two libraries, one patient each** — these are geometries, not a replication cohort. What makes
the headline strong is that two of the arms are the same molecules.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c19ddd3fe15a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.