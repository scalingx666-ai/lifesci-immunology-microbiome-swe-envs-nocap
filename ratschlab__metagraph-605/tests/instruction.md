# Issue

**Title:** Parallel BRWT query in one traversal

## Description

Significantly speeds up queries in large graphs loaded with memory mapping ().

## Query Performance Benchmarks

The following benchmarks compare several Metagraph query implementations across
multiple datasets. Results show the **mean ± standard deviation** across runs,
with the standard deviation also reported as a **percentage of the mean**.

<details>

<summary>Code for the benchmark</summary>

```bash
wait_for_low_cpu() {
    while true; do
        cpu=$(mpstat 1 1 | awk '/Average/ && $2=="all" {print 100-$12}')
        cpu=${cpu%.*}   # optional: drop decimals

        if (( cpu < 5 )); then
            break
        fi

        echo "CPU load ${cpu}% > 5%, sleeping 30s..."
        sleep 30
    done
}

for M in {metagraph_DNA_master,metagraph_DNA_paral4,metagraph_DNA_newBRWT,metagraph_DNA_new10k,metagraph_DNA_new,}; do
for x in {1..5}; do
    wait_for_low_cpu
    /usr/bin/time -v ~/metagraph/metagraph/build/$M query /data/random_stud/queries/100_studies_5k_short.fq -p 30 -v -i /scratch/nvme0/all_sra/data/superkingdom_bacteria/0052/graph.primary.small.dbg -a /scratch/nvme0/all_sra/data/superkingdom_bacteria/0052/annotation.clean.row_diff_brwt.annodbg -v --batch-size 1000000000  2>&1 1>/dev/null | grep -A 3 "Query annotation with" >>logs.txt
    echo -e "\n" >>logs.txt
done

for x in {1..5}; do
    wait_for_low_cpu
    /usr/bin/time -v ~/metagraph/metagraph/build/$M query --query-mode counts /data/random_stud/queries/100_studies_5k_short.fq -p 30 -v -i /scratch/nvme/all_sra/data/kingdom_fungi_RNA/0012/graph.primary.small.dbg -a /scratch/nvme/all_sra/data/kingdom_fungi_RNA/0012/annotation.clean.row_diff_int_brwt.annodbg -v --batch-size 1000000000  2>&1 1>/dev/null | grep -A 3 "Query annotation with" >>logs.txt
    echo -e "\n" >>logs.txt
done

for x in {1..5}; do
    wait_for_low_cpu
    python3 /data/scratch/drop_caches.py /scratch/nvme0/human/graph_merged_complete_k31.primary.small.indexed.dbg
    python3 /data/scratch/drop_caches.py /scratch/nvme7/human/annotation_10.row_diff_flat.annodbg
    /usr/bin/time -v ~/metagraph/metagraph/build/$M query --mmap /data/random_stud/queries/100_studies_50_short.fq -p 30 -v -i /scratch/nvme0/human/graph_merged_complete_k31.primary.small.indexed.dbg -a /scratch/nvme7/human/annotation_10.row_diff_flat.annodbg --min-kmers-fraction-label 0.0 --query-mode matches  2>&1 1>/dev/null | grep -A 3 "Query annotation with" >>logs.txt
    echo -e "\n" >>logs.txt
done

for x in {1..5}; do
    wait_for_low_cpu
    python3 /data/scratch/drop_caches.py /scratch/nvme4/plants/graph_primary.small.indexed.dbg
    python3 /data/scratch/drop_caches.py /scratch/nvme4/plants/*.row_diff_brwt.annodbg
    /usr/bin/time -v ~/metagraph/metagraph/build/$M query --mmap -i /scratch/nvme4/plants/*indexed.dbg -a /scratch/nvme4/plants/*.row_diff_brwt.annodbg /data/scratch/covid.fa -v -p 10 --min-kmers-fraction-label 0.0 --query-mode matches  2>&1 1>/dev/null | grep -A 3 "Query annotation with" >>logs.txt
    echo -e "\n" >>logs.txt
done

for x in {1..5}; do
    wait_for_low_cpu
    python3 /data/scratch/drop_caches.py /scratch/nvme4/plants/graph_primary.small.indexed.dbg
    python3 /data/scratch/drop_caches.py /scratch/nvme4/plants/*.row_diff_brwt.annodbg
    /usr/bin/time -v ~/metagraph/metagraph/build/$M query --mmap -i /scratch/nvme4/plants/*indexed.dbg -a /scratch/nvme4/plants/*.row_diff_brwt.annodbg /data/scratch/plants_query.fa -v -p 10 --min-kmers-fraction-label 0.0 --query-mode matches  2>&1 1>/dev/null | grep -A 3 "Query annotation with" >>logs.txt
    echo -e "\n" >>logs.txt
done
done
```
</details>

---

### all_sra / superkingdom_bacteria — 100_studies_5k_short.fq, 122,725,698 bp, in RAM, 30 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 10 | **6.328 ± 0.136 (2.1%)** | 114.307 ± 6.699 (5.9%) | 1,072,622 ± 59,818 (5.6%) |
| newBRWT | 10 | 7.391 ± 0.133 (1.8%) | **112.606 ± 1.089 (1.0%)** | **1,085,264 ± 11,543 (1.1%)** |

---

### all_sra / kingdom_fungi_RNA + counts — 100_studies_5k_short.fq, 122,725,698 bp, in RAM, 30 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 10 | **8.436 ± 0.133 (1.6%)** | **123.267 ± 0.976 (0.8%)** | **990,197 ± 7,797 (0.8%)** |
| newBRWT | 10 | 9.733 ± 0.350 (3.6%) | 124.984 ± 0.847 (0.7%) | 976,594 ± 6,613 (0.7%) |

---

### human — 100_studies_50_short.fq, 122,725,698 bp, mmap, 30 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 10 | **43.5 ± 1.4 (3.1%)** | **64.6 ± 1.5 (2.3%)** | **18,977 ± 433 (2.3%)** |
| newBRWT | 10 | 47.0 ± 5.7 (12.2%) | 68.8 ± 5.6 (8.1%) | 17,919 ± 1,345 (7.5%) |

---

Now queries on a huge SRA-Plants graph with 1.4 TB annotation

### plants — covid.fa, 29,903 bp (only 16 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 10 | 40.6 ± 3.7 (9.2%) | 57.2 ± 3.7 (6.5%) | 524.2 ± 31.7 (6.0%) |
| newBRWT | 10 | **32.9 ± 4.8 (14.6%)** | **49.5 ± 4.9 (9.8%)** | **607.9 ± 49.0 (8.1%)** |


### plants — plants_query.fa, 16,573 bp (16,408 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 10 | **104.2 ± 0.7 (0.7%)** | **118.6 ± 0.8 (0.6%)** | **139.8 ± 0.9 (0.7%)** |
| newBRWT | 10 | 107.7 ± 4.4 (4.1%) | 122.1 ± 4.5 (3.6%) | 135.9 ± 4.7 (3.4%) |

---

### plants — 100_studies_20_short.fq, 491,594 bp (153,442 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 1 | 498.9 ± — | 553.7 ± — | 888 ± — |
| newBRWT | 1 | **332.8 ± —** | **386.9 ± —** | **1,270 ± —** |

### plants — 100_studies_50_short.fq, 1,226,462 bp (366,859 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 1 | 459.7 ± — | 530.0 ± — | 2,313 ± — |
| newBRWT | 1 | **322.8 ± —** | **395.1 ± —** | **3,102 ± —** |

### plants — 100_studies_100_short.fq, 2,454,716 bp (707,334 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 1 | 446.0 ± — | 551.0 ± — | 4,452 ± — |
| newBRWT | 1 | **318.8 ± —** | **401.9 ± —** | **6,101 ± —** |

### plants — 100_studies_500_short.fq, 12,272,048 bp (3,128,611 k-mer matches), mmap, 10 threads

| Method | Runs | Query annotation (s) | Batch query time (s) | Throughput (bp/s) |
|---|---:|---:|---:|---:|
| new | 1 | 547.7 ± — | 734.3 ± — | 16,673 ± — |
| newBRWT | 1 | **355.0 ± —** | **518.5 ± —** | **23,581 ± —** |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5252bd3346c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.