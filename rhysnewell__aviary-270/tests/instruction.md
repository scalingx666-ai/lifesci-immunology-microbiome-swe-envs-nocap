# Issue

**Title:** Cluster improvements

## Description

- [x] More rules as cluster submission
- [x] Revisit resources

Benchmarks from 1000 coassemblies.
- cpu_time/h in hours
- max_rss/max_vms in GB
- mean_load divided by 100 (so roughly the average # of CPUs in use)

```bash
┌───────────────────────────────┬───────────┬───────┬────────┬───────┐
│ benchmark                     ┆ metric    ┆ min   ┆ median ┆ max   │
│ ---                           ┆ ---       ┆ ---   ┆ ---    ┆ ---   │
│ str                           ┆ str       ┆ f64   ┆ f64    ┆ f64   │
╞═══════════════════════════════╪═══════════╪═══════╪════════╪═══════╡
│ checkm2.benchmark.txt         ┆ cpu_time  ┆ 0.0   ┆ 1.3    ┆ 4.2   │
│ checkm2.benchmark.txt         ┆ h         ┆ 0.0   ┆ 0.1    ┆ 0.3   │
│ checkm2.benchmark.txt         ┆ max_rss   ┆ 5.1   ┆ 14.7   ┆ 19.1  │
│ checkm2.benchmark.txt         ┆ max_vms   ┆ 92.1  ┆ 101.6  ┆ 486.4 │
│ checkm2.benchmark.txt         ┆ mean_load ┆ 0.1   ┆ 13.1   ┆ 19.7  │
│ das_tool.benchmark.txt        ┆ cpu_time  ┆ 0.0   ┆ 1.2    ┆ 4.8   │
│ das_tool.benchmark.txt        ┆ h         ┆ 0.0   ┆ 0.4    ┆ 2.5   │
│ das_tool.benchmark.txt        ┆ max_rss   ┆ 0.3   ┆ 7.0    ┆ 134.1 │
│ das_tool.benchmark.txt        ┆ max_vms   ┆ 7.4   ┆ 33.3   ┆ 215.4 │
│ das_tool.benchmark.txt        ┆ mean_load ┆ 0.0   ┆ 2.4    ┆ 5.9   │
│ metabat_2.benchmark.txt       ┆ cpu_time  ┆ 0.0   ┆ 1.3    ┆ 22.1  │
│ metabat_2.benchmark.txt       ┆ h         ┆ 0.0   ┆ 0.1    ┆ 0.8   │
│ metabat_2.benchmark.txt       ┆ max_rss   ┆ 0.7   ┆ 3.8    ┆ 16.4  │
│ metabat_2.benchmark.txt       ┆ max_vms   ┆ 0.9   ┆ 4.1    ┆ 16.5  │
│ metabat_2.benchmark.txt       ┆ mean_load ┆ 6.3   ┆ 24.5   ┆ 29.1  │
│ metabat_sens.benchmark.txt    ┆ cpu_time  ┆ 0.0   ┆ 2.0    ┆ 46.9  │
│ metabat_sens.benchmark.txt    ┆ h         ┆ 0.0   ┆ 0.1    ┆ 2.2   │
│ metabat_sens.benchmark.txt    ┆ max_rss   ┆ 0.1   ┆ 3.9    ┆ 88.6  │
│ metabat_sens.benchmark.txt    ┆ max_vms   ┆ 2.1   ┆ 6.5    ┆ 105.8 │
│ metabat_sens.benchmark.txt    ┆ mean_load ┆ 0.3   ┆ 22.5   ┆ 31.2  │
│ metabat_spec.benchmark.txt    ┆ cpu_time  ┆ 0.0   ┆ 1.9    ┆ 42.3  │
│ metabat_spec.benchmark.txt    ┆ h         ┆ 0.0   ┆ 0.1    ┆ 2.0   │
│ metabat_spec.benchmark.txt    ┆ max_rss   ┆ 0.1   ┆ 3.6    ┆ 85.3  │
│ metabat_spec.benchmark.txt    ┆ max_vms   ┆ 2.2   ┆ 6.1    ┆ 103.9 │
│ metabat_spec.benchmark.txt    ┆ mean_load ┆ 0.4   ┆ 22.5   ┆ 30.8  │
│ metabat_ssens.benchmark.txt   ┆ cpu_time  ┆ 0.0   ┆ 2.0    ┆ 42.6  │
│ metabat_ssens.benchmark.txt   ┆ h         ┆ 0.0   ┆ 0.1    ┆ 1.9   │
│ metabat_ssens.benchmark.txt   ┆ max_rss   ┆ 0.1   ┆ 4.0    ┆ 88.6  │
│ metabat_ssens.benchmark.txt   ┆ max_vms   ┆ 2.1   ┆ 6.6    ┆ 106.0 │
│ metabat_ssens.benchmark.txt   ┆ mean_load ┆ 0.4   ┆ 22.5   ┆ 30.9  │
│ metabat_sspec.benchmark.txt   ┆ cpu_time  ┆ 0.0   ┆ 1.5    ┆ 36.0  │
│ metabat_sspec.benchmark.txt   ┆ h         ┆ 0.0   ┆ 0.1    ┆ 1.4   │
│ metabat_sspec.benchmark.txt   ┆ max_rss   ┆ 0.1   ┆ 3.5    ┆ 107.3 │
│ metabat_sspec.benchmark.txt   ┆ max_vms   ┆ 2.1   ┆ 5.9    ┆ 147.8 │
│ metabat_sspec.benchmark.txt   ┆ mean_load ┆ 0.3   ┆ 22.8   ┆ 28.5  │
│ metabuli.benchmark.txt        ┆ cpu_time  ┆ 0.1   ┆ 0.9    ┆ 3.9   │
│ metabuli.benchmark.txt        ┆ h         ┆ 0.0   ┆ 0.0    ┆ 0.3   │
│ metabuli.benchmark.txt        ┆ max_rss   ┆ 18.2  ┆ 80.7   ┆ 127.6 │
│ metabuli.benchmark.txt        ┆ max_vms   ┆ 126.3 ┆ 130.7  ┆ 130.7 │
│ metabuli.benchmark.txt        ┆ mean_load ┆ 5.6   ┆ 17.3   ┆ 24.6  │
│ refine_dastool.benchmark.txt  ┆ cpu_time  ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_dastool.benchmark.txt  ┆ h         ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_dastool.benchmark.txt  ┆ max_rss   ┆ 0.1   ┆ 0.1    ┆ 0.1   │
│ refine_dastool.benchmark.txt  ┆ max_vms   ┆ 4.2   ┆ 4.2    ┆ 4.2   │
│ refine_dastool.benchmark.txt  ┆ mean_load ┆ 0.0   ┆ 0.1    ┆ 1.2   │
│ refine_metabat2.benchmark.txt ┆ cpu_time  ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_metabat2.benchmark.txt ┆ h         ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_metabat2.benchmark.txt ┆ max_rss   ┆ 0.0   ┆ 0.1    ┆ 0.1   │
│ refine_metabat2.benchmark.txt ┆ max_vms   ┆ 4.2   ┆ 4.2    ┆ 4.2   │
│ refine_metabat2.benchmark.txt ┆ mean_load ┆ 0.0   ┆ 0.2    ┆ 2.0   │
│ refine_rosella.benchmark.txt  ┆ cpu_time  ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_rosella.benchmark.txt  ┆ h         ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_rosella.benchmark.txt  ┆ max_rss   ┆ 0.0   ┆ 0.1    ┆ 0.1   │
│ refine_rosella.benchmark.txt  ┆ max_vms   ┆ 4.2   ┆ 4.2    ┆ 4.2   │
│ refine_rosella.benchmark.txt  ┆ mean_load ┆ 0.0   ┆ 0.4    ┆ 1.4   │
│ refine_semibin.benchmark.txt  ┆ cpu_time  ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_semibin.benchmark.txt  ┆ h         ┆ 0.0   ┆ 0.0    ┆ 0.0   │
│ refine_semibin.benchmark.txt  ┆ max_rss   ┆ 0.1   ┆ 0.1    ┆ 0.1   │
│ refine_semibin.benchmark.txt  ┆ max_vms   ┆ 4.2   ┆ 4.2    ┆ 4.2   │
│ refine_semibin.benchmark.txt  ┆ mean_load ┆ 0.0   ┆ 0.1    ┆ 0.5   │
│ rosella.benchmark.txt         ┆ cpu_time  ┆ 0.0   ┆ 0.2    ┆ 92.1  │
│ rosella.benchmark.txt         ┆ h         ┆ 0.0   ┆ 0.1    ┆ 5.4   │
│ rosella.benchmark.txt         ┆ max_rss   ┆ 1.1   ┆ 58.0   ┆ 134.8 │
│ rosella.benchmark.txt         ┆ max_vms   ┆ 3.4   ┆ 136.1  ┆ 302.4 │
│ rosella.benchmark.txt         ┆ mean_load ┆ 0.3   ┆ 0.9    ┆ 30.0  │
│ semibin.benchmark.txt         ┆ cpu_time  ┆ 2.1   ┆ 9.5    ┆ 16.6  │
│ semibin.benchmark.txt         ┆ h         ┆ 0.1   ┆ 0.6    ┆ 2.3   │
│ semibin.benchmark.txt         ┆ max_rss   ┆ 17.4  ┆ 69.8   ┆ 266.5 │
│ semibin.benchmark.txt         ┆ max_vms   ┆ 180.8 ┆ 536.8  ┆ 737.5 │
│ semibin.benchmark.txt         ┆ mean_load ┆ 4.9   ┆ 16.0   ┆ 22.8  │
│ taxvamb.benchmark.txt         ┆ cpu_time  ┆ 0.0   ┆ 5.9    ┆ 26.2  │
│ taxvamb.benchmark.txt         ┆ h         ┆ 0.0   ┆ 1.0    ┆ 4.3   │
│ taxvamb.benchmark.txt         ┆ max_rss   ┆ 0.7   ┆ 16.5   ┆ 31.0  │
│ taxvamb.benchmark.txt         ┆ max_vms   ┆ 17.9  ┆ 152.5  ┆ 189.6 │
│ taxvamb.benchmark.txt         ┆ mean_load ┆ 1.9   ┆ 5.6    ┆ 13.0  │
│ vamb.benchmark.txt            ┆ cpu_time  ┆ 5.2   ┆ 92.9   ┆ 457.7 │
│ vamb.benchmark.txt            ┆ h         ┆ 0.2   ┆ 3.0    ┆ 14.8  │
│ vamb.benchmark.txt            ┆ max_rss   ┆ 0.7   ┆ 1.4    ┆ 2.1   │
│ vamb.benchmark.txt            ┆ max_vms   ┆ 19.4  ┆ 20.0   ┆ 20.7  │
│ vamb.benchmark.txt            ┆ mean_load ┆ 24.3  ┆ 30.7   ┆ 31.5  │
└───────────────────────────────┴───────────┴───────┴────────┴───────┘
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `657d966ff440`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.