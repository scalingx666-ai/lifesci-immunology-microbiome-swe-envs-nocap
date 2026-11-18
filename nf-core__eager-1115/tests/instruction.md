# Issue

**Title:** DSL2 restructure output directories

## Description

Tested with profiles:
- [x] test
- [x] test_humanbam
- [x] test_kraken2
- [x] test_krakenuniq
- [x] test_malt
- [x] test_metaphlan
- [x] test_multiref
- [x] test_nothing
- [ ] ~test_full~ (DSL1)

# Changes
- Restructrued all output directories to `section/tools/{data/stats}` structure.
- Also reordered the order of modules by section and relative order of operation/appearance.
- Fixed a small bug in preseq lc_extrap. ()

This works fine for test profile (as fa as I could see), but some moduels (e.g. `damageprofiler`, `qualimap`) break the system by having results be a subdirectory.

```
$ tree results/ -d
results/
├── authentication
│   ├── bedtools
│   │   └── stats
│   ├── damageprofiler
│   │   └── stats
│   │       ├── JK2782_JK2782_TGGCCGATCAACGA_BAM_Mammoth_MT_Krause
│   │       ├── JK2782_JK2782_TGGCCGATCAACGA_Mammoth_MT_Krause
│   │       └── JK2802_JK2802_AGAATAACCTACCA_Mammoth_MT_Krause
│   ├── endorspy
│   │   └── stats
│   ├── preseq
│   │   └── stats
│   └── qualimap
│       └── stats
│           └── Mammoth_MT_Krause
│               ├── JK2782
│               │   ├── css
│               │   ├── images_qualimapReport
│               │   └── raw_data_qualimapReport
│               └── JK2802
│                   ├── css
│                   ├── images_qualimapReport
│                   └── raw_data_qualimapReport
├── deduplication
│   └── markduplicates
│       ├── data
│       └── stats
├── final_bams
│   └── raw
│       ├── data
│       └── stats
├── mapping
│   ├── bam_input
│   │   └── stats
│   └── bwaaln
│       ├── data
│       └── stats
├── multiqc
│   ├── multiqc_data
│   └── multiqc_plots
│       ├── pdf
│       ├── png
│       └── svg
├── pipeline_info
├── preprocessing
│   ├── fastp
│   │   └── stats
│   ├── fastqc_processed
│   │   └── stats
│   └── fastqc_raw
│       └── stats
└── read_filtering
    └── filtered_bams
        ├── data
        └── stats

56 directories
```

Those will likely need some tweaking to work without filename collisions.

<!-- markdownlint-disable ul-indent -->

## PR checklist

- [x] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
    - [ ] If you've added a new tool - add to the software_versions process and a regex to `scrape_software_versions.py`
    - [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](<https://github.com/>nf-core/eager/tree/master/.github/CONTRIBUTING.md)
    - [ ] If necessary, also make a PR on the nf-core/eager _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [x] Make sure your code lints (`nf-core lint .`).
- [x] Ensure the test suite passes (`nextflow run . -profile test,docker`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b87fc57a61b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.