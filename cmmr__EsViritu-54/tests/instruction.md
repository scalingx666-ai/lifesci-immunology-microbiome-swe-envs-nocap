# Issue

**Title:** Read share threshold

## Description

**Title:** add --read-share-threshold for assembly clustering

Hi Mike, this makes the read-sharing cutoff used to cluster candidate assemblies (`cluster_assemblies_by_read_sharing`, fixed at 0.33) configurable from the command line. **The default stays 0.33, so existing runs give identical output.**

### Changes

- `EsViritu.py`: new `--read-share-threshold` (float, default 0.33), passed to both clustering steps. It's recorded in `<SAMPLE>_esviritu.params.yaml` like the other options.
- `docs/pipeline-description.md`: step 3 said the shared fraction is over the union of read IDs. The code divides by the reference with fewer aligned reads (`n_shared / min(total_reads_a, total_reads_b)`), so I updated the wording and pointed to the option.

### Why

In samples with several strains of one species at uneven abundance, the cutoff sets how rare a minor strain can be and still be reported as its own call. Users with mixed-strain samples (wastewater, for us) can raise it to resolve rarer strains. Others can keep 0.33, which is better at stopping close sibling references from competing for reads. Neither value is right for every dataset, so it seemed worth exposing rather than changing.

### Test

Simulated 2×150 reads (wgsim, 0.2% error, fixed seeds), DB v3.2.4, `-q False -f False`. HAdV-21 (`KF528688`) is fixed at 4,000 reads, and HAdV-3 (`EF564601`) varies. Each cell shows how the HAdV-3 reads were reported.

| HAdV-3 reads (ratio) | shared fraction | v1.3.5 | 0.33 | 0.40 | 0.50 | 0.60 |
|---|---|---|---|---|---|---|
| 4,000 (1:1) | 0.22 | `EF564601` 3,992 | same | same | same | same |
| 2,000 (1:2) | 0.31 | `EF564601` 1,998 | same | same | same | split: `GCF_000880515.1` 1,571 + `GCF_000857085.1` 433 |
| 1,200 (1:3.3) | 0.39 | clustered into `KF528688` | same | `EF564601` 1,198 | `EF564601` 1,198 | `EF564601` 1,198 |
| 480 (1:8) | 0.56 | clustered into `KF528688` | same | `GCF_000857085.1` 125 | same | `EF564601` 482 |
| 240 (1:17) | 0.70 | clustered into `KF528688` | same | `GCF_000857085.1` 70 | same | same |
| HAdV-3 only (4,000) | spillover 1.0 | `EF564601` 4,000 | same | same | same | same |

- With the default, the branch matches v1.3.5 in every sample.
- A minor strain is kept as its own call exactly when its shared fraction is below the threshold.
- The cost of raising it shows at 0.60 in the 1:2 sample, and at 0.40–0.50 for the rarest strains. Near-identical HAdV-B references (`GCF_000857085.1`, `GCF_000880515.1`) survive clustering and take the minor strain's reads.

This is one strain pair on simulated reads, so it supports making the value adjustable, not a different default.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ea68d8d7c641`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.