# Issue

**Title:** Add 'num reads mapped' tables to profile database

## Description

With my latest updates to the discov formula it became necessary for profile databases to store the number of reads mapped to each contig (and split), in order to use these in downstream calculations. This PR adds three tables and a new self key to the profile database to store this data, bumps the DB version to 43, and includes a migration script to add the empty tables.

In addition, it fixes one bug with the previous migration (tables for contigs/splits with zero coverage): contigs that have reads mapping to them but for which all reads are filtered out (due to parameters like --min-percent-identity or fetch filters, or because they don't include a sequence in the BAM file) yielding effective zero values for coverage and other stats _used to be_ stored in the regular view tables with explicit zeros, but these are now moved to the zero_coverage_contigs table. The migration script handles this move as well.

## Detailed changes
Here are more details, as summarized by Claude (and amended by me):

### How reads are counted

  - The counting happens in `bamops.Coverage.run`, in the same pass over the reads that builds the coverage array, so it does not add a second pass over the BAM file.
  - Each read is assigned to **exactly one split**: the one that contains most of its aligned bases (from `get_blocks()`, the same bases that count toward coverage). An exact tie goes to the earlier split. Reads that do not cross a split boundary are assigned by a quick `bisect` lookup. Only reads that cross a boundary need their aligned bases counted per split.
  - Because of this, the split counts of a contig always add up to the contig's count. Coverage is different: a read that crosses a boundary adds depth to both splits.
  - Also because of this, it can happen that splits with mapped reads that _all_ are primarily located in a _different_ split will have a count of 0. To distinguish these from the 'true 0s' (for which the contig and all its splits are stored in the zero_coverage tables), we need an extra table to store these split names
  - `contigops.Contig.analyze_coverage` passes the split boundaries in and gives each split its count. A contig with a single split simply takes the contig's count.

### New profile database tables

  | Table | Contents |
  |---|---|
  | `num_reads_assigned_splits` | number of reads assigned to each split |
  | `num_reads_mapped_contigs` | number of reads mapped to each contig |
  | `zero_num_reads_assigned_splits` | (item, layer) pairs for splits that **have coverage but no assigned reads**, because every read touching them has most of its aligned bases in a neighbouring split |

These tables use the same structure as view tables but are not registered as views, so they don't show up in the interface and are not used for clustering. Zeros are not stored explicitly, the same as in the other view tables. When `get_view_data` reads these tables, it fills in zeros from:
  - `zero_coverage_splits` / `zero_coverage_contigs` (no coverage means no reads), and
  - `zero_num_reads_assigned_splits`, which applies only to the split read-count table.

A new `self` table key, `num_reads_mapped_stored`, records whether the counts exist. It is true for normal profiles. It is false for blank profiles and for databases migrated from v42. Profile databases without the key, such as ad hoc ones, are treated as false. This key can be used downstream to sanity check that num read data are available before attempting calculations requiring this data.

Other table-related updates:
- `db.py` has two new helper functions, `get_zero_value_tables_for_view_table` / `get_zero_value_dict_for_view_table`, used by both `get_view_data` paths, to find which zero tables apply to a given view table (since we now have multiple possibilities corresponding to num_reads_assigned_splits)
- `anvi-merge` checks `num_reads_mapped_stored` and will not merge two profile DBs with different values in that self key
- `anvi-merge` merges the new tables, following the same strategy as zero_coverage tables for zero_num_reads_assigned_splits, and the same strategy as the other view tables for the other num_reads tables
- in `anvi-split`, the three new tables are subset per bin. A contig whose splits are spread over several bins keeps its full contig count in each of those bins.

### An extra fix: Contigs with zero coverage now go into `zero_coverage_contigs`

Until now, a contig that was profiled but ended up with no coverage got explicit zero rows in every `*_contigs` view table. This can happen when filters remove all of its reads, or when the BAM index counts alignments that have no CIGAR or no sequence. I discussed the solution to this with @FlorianTrigodet earlier today and he agreed that I could include this in the current PR. Such contigs, and all of their splits, now go into the zero-coverage tables, the same way as contigs skipped by the BAM index prefilter. `get_view_data` returns the same values as before.

### Database version and migration

The profile database version goes from **42 → 43**. The migration script, `v42_to_v43`, does two things:
  1. It creates the three new tables, empty, and sets `num_reads_mapped_stored` to false. Read counts cannot be recovered from existing data, so you need to re-profile if you want them.
  2. It moves explicit zero-detection rows of splits and contigs from the view tables into the zero-coverage tables, so that migrated databases match newly profiled ones. The strategy for this matches what was done in the `v41_to_v42` migration script.
     - It first checks that these items are zero in every view table. Any that are not are left in place, with a warning.
     - All changes are made in a single transaction, and the database is only vacuumed if something was moved.

## Testing that Claude did
- Compared every read's assignment with a brute-force pysam calculation on the sandbox data, including ties: no differences. The split counts add up to the contig counts, which match `anvi-profile-blitz` and `total_reads_kept`.
- Built a synthetic test set: a FASTA file and contigs DB with split length 1000 and no gene calls, plus four BAM files. The counts anvi'o stores match independently calculated expected counts in every case:
    - every split has reads (including reads that cross boundaries, and some reads with mismatches to test `--min-percent-identity`);
    - splits with no reads, both inside covered contigs and as a whole contig;
    - splits covered only by reads that mostly align elsewhere, which end up in `zero_num_reads_assigned_splits`, plus a 50/50 tie read and a read with a long deletion;
    - a sample with no reads at all.
- `anvi-merge` with all samples: row counts match the inputs, and each sample's counts are kept exactly. Merging migrated profiles without counts works; mixing profiles with and without counts is refused.
- `anvi-split` with a collection that includes a contig spread over two bins: the count tables and zero tables are subset correctly for every bin.
- Migrating v42 databases leaves the output of `get_view_data` unchanged.
- `anvi-self-test` passes

## Testing that I did

I used Claude's script `make_test_data.py` to generate the synthetic data:
[make_test_data.py](https://github.com/user-attachments/files/34046560/make_test_data.py)

```
python make_test_data.py
anvi-gen-contigs-database -f contigs.fa -o CONTIGS.db -L 1000 --skip-gene-calling
# generate profiles with read counts
anvi-profile -c CONTIGS.db -i S1_all_splits.bam -o S1
anvi-profile -c CONTIGS.db -i S1_all_splits.bam -o S1_95 --min-percent-identity 95 -S S1_95_min_id
anvi-profile -c CONTIGS.db -i S2_missing_splits.bam -o S2
anvi-profile -c CONTIGS.db -i S3_minority_splits.bam -o S3
anvi-profile -c CONTIGS.db -i S4_no_reads.bam -o S4
# test the merge
anvi-merge S*/PROFILE.db -c CONTIGS.db -o MERGED

# test splitting
anvi-import-collection collection.txt -p MERGED/PROFILE.db -c CONTIGS.db -C test_bins
anvi-split -p MERGED/PROFILE.db -c CONTIGS.db -C test_bins -o SPLIT
```

I manually cross-checked between the merged profile and the table of expected read counts to make sure they matched, especially for the critical edge cases like splits with 0 counts. I also manually checked one of the split DBs to make sure the data for that bin was correctly carried over.

Then I switched back to master and made a v42 profile DB from one of the BAM files, switched back to test the migration, and attempted to merge with a profile that had read count data to make sure it failed:
```
# in master
anvi-profile -c CONTIGS.db -i S1_all_splits.bam -o S1_master -S S1_master
# in branch
anvi-migrate --migrate-safely S1_master/PROFILE.db
anvi-merge -c CONTIGS.db S1/PROFILE.db S1_master/PROFILE.db -o test_bad_merge
```

It seems like this is good to go but I would like another pair of eyes on it before it is merged :)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15db5935566a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.