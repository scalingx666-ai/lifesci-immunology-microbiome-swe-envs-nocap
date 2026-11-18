# Issue

**Title:** Map coords to headers in align with CoordToHeader

## Description

Resolves global k-mer coordinates to per-sequence `header:start-end` labels in `metagraph align`, via a `.seqs` index (`CoordToHeader`) built by `--index-header-coords` at annotation time.

When an alignment's coordinate range crosses a sequence boundary in the index (the graph path continues from the last k-mer of one indexed sequence into the first of the next via a shared prefix), the label is split across headers and joined with `;`:

```
seq1:5-12;seq2:1-8
```

## How this fits in the alignment landscape

`metagraph align` has several regimes depending on annotation type and aggregation. The last column names which produces the row this PR is about:

| # | Aligner | Annotator | Aggregation | `.seqs` | CIGARs / query | Label example |
|---|---------|-----------|-------------|---------|----------------|---------------|
| 1 | `DBGAligner` | none | — | — | 1 | *none* |
| 2 | `LabeledAligner` | column (no coords) | per-seq (`--anno-header`) | — | ≤ #seqs | `seq1`, `seq2` |
| 3 | `LabeledAligner` | column (no coords) | per-file (`--anno-filename`) | — | 1 | `file.fa` |
| 4 | `LabeledAligner` | coord | per-seq (`--anno-header`) | — | ≤ #seqs | `seq1:1-9` |
| 5 | `LabeledAligner` | coord | per-file (`--anno-filename`) | no | 1 | `file.fa:3-9:23-30` |
| 6 | `LabeledAligner` | coord | per-file (`--anno-filename`) | **yes** | 1 | `seq1:3-9;seq3:1-8` |

This PR introduces mode **#6** and wires `.seqs` through to `format_coords` so the label column can report per-sequence ranges while the annotator keeps the file-level aggregation.

## What's new

- `CoordToHeader::num_kmers_in_sequence(col, seq_id)` — per-sequence k-mer count derived from the existing `coord_offsets_` bit vector.
- `Alignment::format_coords` split into two typed overloads: `format_coords(encoder)` and `format_coords(cth, k)`. The caller (`cli/align.cpp`) picks the right one; `Alignment` itself stays data-only.
- `CoordToHeader::map_single_coord(col, coord) -> (seq_id, local_coord)` single-coord accessor alongside the batched `map_to_local_coords`.
- `--no-coord-mapping` flag to keep the global `file:offset` labels (bypasses `.seqs`).
- Out-of-range inputs in `CoordToHeader` uniformly throw `std::out_of_range`.

## Output semantics (documented on `format_coords`)

```
"<label>:<start>-<end>[:<start>-<end>...][;<label>:...]"
```

- `';'` separates labels; `':'` separates the label from its ranges and ranges from each other.
- Ordering: labels appear in first-seen order walking `label_coordinates` (by column, then by starting coord).
- With the `(cth, k)` overload, a range crossing a sequence boundary in the `.seqs` index is split across consecutive sequences, each getting its own range.

## Tests

- Unit (`test_coord_to_header.cpp`): accessor consistency and out-of-range behavior, serialize/load round-trip, `format_coords` overloads, and cross-boundary edge cases (exact fill, full-column span, overflow past last sequence, 2- and 3-sequence chains, multiple coords spilling into the same next sequence).
- End-to-end aligner (`test_aligner_labeled.cpp`, `LabeledAlignerCoordTest` fixture): 2- and 3-sequence cross-boundary alignments with exact match, indels, shared-k-mer partial coverage, and reverse-complement.
- Integration (`integration_tests/test_align.py`): basic mapping, `--no-coord-mapping`, multi-label, multi-file, mismatch CIGAR, and equivalence between mode #6 (`--anno-filename + .seqs`) and mode #4 (`--anno-header`) for both single- and two-file inputs.

## Follow-up (out of scope)

Making mode #6 emit distinct CIGARs for sequences within a single file that have divergent extension paths would require slicing the annotator into virtual per-sequence sub-columns before `LabeledAligner` extends — a bigger design change noted in the `TestAlignCoordToHeader` class docstring.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `124cbab2407f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.