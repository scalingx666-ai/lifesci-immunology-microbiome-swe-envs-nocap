# Issue

**Title:** Decode the rows of a query by record in blocks

## Description

On an index with a `.seqs` file, a query decoded the annotation rows of all its k-mers at once and kept them until the cut to the top records. A row holds a coordinate for every record that contains its k-mer, so the rows took far more memory than the answer. A 5 kb query on 20,000 similar records held 655 MiB of rows for a 0.4 kB answer.

## The change

The rows are decoded 256 at a time and folded into the records. Each record met keeps its count and, for `signature`, `counts` and `coords`, its values as runs of query positions. Only the records returned are expanded. `matches`, `signature`, `counts` and `coords` share this fold.

`CoordToHeader::map_coords` maps the coordinates of a row to records. They are sorted, so the next record is usually the same or the following one, and it is found in a table of the column's sequence starts. It replaces `map_to_local_coords`, which had no other caller and took a rank and a select per coordinate.

## Behaviour changes

- Records that are not cut to the top N come in the order of their first matching query position. They came in the iteration order of a hash set. Results cut to the top N keep their order.
- A sequence of 2^32 or more k-mers is refused when queried by record.

## Memory: two different figures

**Per query, it falls.** The peak of one 5 kb query goes from 721 MiB to 122 MiB (table below). That memory is freed when the query ends.

**Per server, a table is added.** `map_coords` keeps the sequence starts of every column it has been asked about: 8 bytes per record, built on the first query that touches the column, held until the server exits. It is shared by all queries and does not grow with the number of queries.

| Index | Columns | Records | Server memory today | Table per column touched | Table once every column is touched |
|---|---|---|---|---|---|
| AllTheBacteria | 1,027 | 448 million | 30.6 GB | 3.5 MB on average | 3.6 GB (+12%) |
| UniParc | 200 | 541 million | 22.6 GB | 21.6 MB on average | 4.3 GB (+19%) |

"Server memory today" is the resident memory of the two `server_query` processes on our host, 2.5 hours after a restart, with the graph and annotation memory-mapped. Most of it is the record index itself (28 GB and 17 GB when loaded alone). The host has 1,133 GB.

Other databases, from the record counts in our catalog: RefSeq has 63.7 million records, so at most 0.5 GB. Tara Oceans (scaffolds) has 318 million scaffolds, so at most 2.5 GB if it is served with a record mapping, which I have not confirmed. Indexes without a `.seqs` file, such as the SRA and Logan chunk indexes, get no table.

The last column is the upper bound. How fast a server approaches it depends on which columns its queries hit, which I have not measured. Two mappings without the table were measured and are slower (5 kb `coords`, before the review fix: 2.85 s with a cursor over the Elias-Fano high bits, 3.39 s with one select per record, against 2.10 s).

## Measurements

mex, GCC 13.3, Release, `metagraph query`, `row_diff_brwt_coord` with a `.seqs` file, 20,000 records of 5 kb that differ in 1% of bases. Load average below 4.

5 kb query, top 1, one thread:

| Mode | Time before | Time after | Peak RSS before | Peak RSS after |
|---|---|---|---|---|
| `coords` | 5.97 s | 2.44 s | 721 MiB | 123 MiB |
| `matches` | 5.29 s | 1.65 s | 721 MiB | 103 MiB |
| `signature` | 7.32 s | 2.13 s | 720 MiB | 124 MiB |
| `counts` | 7.34 s | 2.13 s | 721 MiB | 123 MiB |

2,000 reads of 150 bp: 16 threads, `coords` 21.1 s to 8.5 s and `matches` 17.4 s to 5.0 s, with 386 to 426 MiB and 389 to 416 MiB. One thread, `coords` 278 s to 89 s. The read rows were measured before the review fix, which costs `coords` about 0.3 s on the 5 kb query.

Records that repeat a unit (3,000 records of 8 copies of a 600 bp unit, a query of 3 copies, top 1): `coords` 1.66 s and 298 MiB to 0.63 s and 99 MiB, `matches` 0.57 s and 137 MiB to 0.21 s and 91 MiB.

Output against master, 636 runs (6 query modes, top 1 to 100,000, two thresholds, four indexes with one and three columns, text, `--json`, `--verbose-output`, `--batch-size 0`): 245 give the same bytes. The other 391 return records that are not cut, and give the same records in the new order.

## What it does not do

- A record met keeps its runs until the end, also when it is not returned. A query that matches very many records at scattered positions can hold up to twice the bytes of its rows.
- For short reads the rows of one read are small, so their memory does not change.
- Queries by annotation column (no `.seqs` file) are unchanged.

Reuse: `top_n_sorted` and `map_to_rows` are reused. The per-column record lookup is new: `utils::ValueStore` sizes its array by the column, which is 436,000 records per column on the AllTheBacteria index. The fold builds runs itself, as `CountRuns` does, because a position's count still grows while its row is read.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated description by cubic. -->
<a href="https://cubic.dev/pr/ratschlab/metagraph/pull/764?utm_source=github" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/review-in-cubic-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/review-in-cubic-light.svg"><img alt="View guided diff" src="https://www.cubic.dev/buttons/review-in-cubic-light.svg"></picture></a> <a href="https://www.cubic.dev/action/auto-fix/pr/ratschlab/metagraph/764?returnTo=https%3A%2F%2Fgithub.com%2Fratschlab%2Fmetagraph%2Fpull%2F764&source=description" target="_blank" rel="noopener noreferrer" data-no-image-dialog="true"><picture><source media="(prefers-color-scheme: dark)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"><img alt="Turn on auto-fix" src="https://www.cubic.dev/buttons/turn-on-auto-fix-light.svg"></picture></a>
<!-- End of auto-generated description by cubic. -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70f9711739a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.