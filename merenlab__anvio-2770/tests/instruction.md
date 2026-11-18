# Issue

**Title:** Taxonomy display, as tree

## Description

This PR adds a feature that will dramatically simplify the lives of us who often survey taxonomic insights into metagenomes through SCGs.

For instance, this is what one typically sees when they run `anvi-estimate-scg-taxonomy` on a contigs-db file with `--metagenome-mode`:

```
anvi-estimate-scg-taxonomy -c Sample_01.db --metagenome-mode
Contigs DB ...................................: Sample_01.db
Metagenome mode ..............................: True
(...)

Taxa in metagenome "Sample_01"
===============================================
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
|                                |   percent_identity | taxonomy                                                                                                                                  |
+================================+====================+===========================================================================================================================================+
| Sample_01_Ribosomal_S11_102879 |                100 | Bacteria / Campylobacterota / Campylobacteria / Campylobacterales / Sulfurovaceae / Sulfurovum / Sulfurovum sp021159425                   |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_10895  |                 95 | Bacteria / Bacillota_A / Clostridia / Clostridiales / Clostridiaceae / Clostridium / Clostridium sp012519155                              |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_136641 |               95.3 | Bacteria / Campylobacterota / Campylobacteria / Campylobacterales / Sulfurovaceae / Sulfurovum / Sulfurovum sp013607775                   |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_140713 |               94.5 | Bacteria / Bacillota_A / Clostridia / DUPQ01 / DUPQ01 / JAFGQE01 /                                                                        |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| (...) ONE GAZILLION MORE ENTRIES (...)
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_92474  |                100 | Bacteria / Pseudomonadota / Gammaproteobacteria / Beggiatoales / Beggiatoaceae / QNES01 / QNES01 sp003645255                              |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_93731  |                100 | Bacteria / Campylobacterota / Campylobacteria / Campylobacterales / Sulfurovaceae / Sulfurovum / Sulfurovum sp013607775                   |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Sample_01_Ribosomal_S11_99080  |               96.8 | Bacteria / Campylobacterota / Campylobacteria / Campylobacterales / Sulfurovaceae /  /                                                    |
+--------------------------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
```

Which makes it extremely difficult to get a quick idea about what phyla or genera or anything that is represented more in the assembly than others.

This PR adds a `--tree-output` for such applications. In this case, the user sees something like this for the same sample:

```
anvi-estimate-scg-taxonomy -c Sample_01.db --metagenome-mode --tree-output
Contigs DB ...................................: Sample_01.db
Metagenome mode ..............................: True
(...)

Taxa in metagenome "Sample_01"
===============================================

All Ribosomal_S11 copies (96)
├── Bacteria (94)
│   ├── Campylobacterota (36)
│   │   └── Campylobacteria (36)
│   │       └── Campylobacterales (36)
│   │           ├── Sulfurovaceae (33)
│   │           │   ├── Sulfurovum (32)
│   │           │   └── Unknown_genera (1)
│   │           └── Sulfurimonadaceae (3)
│   │               ├── Unknown_genera (2)
│   │               └── Sulfurimonas (1)
│   ├── Desulfobacterota (16)
│   │   ├── Desulfobulbia (9)
│   │   │   └── Desulfobulbales (9)
│   │   │       ├── Desulfocapsaceae (4)
│   │   │       │   ├── Desulfocapsa (2)
│   │   │       │   └── Desulfomarina (2)
│   │   │       ├── Desulfobulbaceae (3)
│   │   │       │   └── Desulfobulbus_C (3)
│   │   │       └── Desulfurivibrionaceae (2)
│   │   │           └── JAGHCC01 (2)
│   │   ├── Desulfobacteria (3)
│   │   │   └── Desulfobacterales (3)
│   │   │       ├── 4be13 (2)
│   │   │       │   └── Desulfonema_C (2)
│   │   │       └── UBA11574 (1)
│   │   │           └── S5133MH16 (1)
│   │   ├── Dissulfuribacteria (2)
│   │   │   └── Dissulfuribacterales (2)
│   │   │       └── UBA3076 (2)
│   │   │           └── UBA3076 (2)
│   │   └── DSM-4660 (2)
│   │       └── Desulfatiglandales (2)
│   │           └── Desulfatiglandaceae (2)
│   │               └── 4484-190-2 (2)
│   ├── Bacteroidota (13)
│   │   └── Bacteroidia (13)
│   │       ├── Flavobacteriales (7)
│   │       │   ├── Flavobacteriaceae (6)
│   │       │   │   ├── Lutimonas (4)
│   │       │   │   └── Flavicella (2)
│   │       │   └── JAHECK01 (1)
│   │       │       └── JAHECK01 (1)
│   │       └── Bacteroidales (6)
│   │           ├── GCA-2748055 (2)
│   │           │   └── GCA-2748055 (2)
│   │           ├── NBLH01 (2)
│   │           │   └── NBLH01 (2)
│   │           ├── JAADGE01 (1)
│   │           │   └── JAADGE01 (1)
│   │           └── VadinHA17 (1)
│   │               └── JANTGF01 (1)
│   └── (... OTHER BACTERIAL PHYLA ....)
└── Archaea (2)
    └── Halobacteriota (2)
        └── Methanosarcinia (2)
            └── Methanosarcinales (2)
                └── Methanogasteraceae (2)
                    └── Methanogaster (2)
```

The user can even limit at what level they wish to see this tree using the flag `--tree-output-level`:

```
anvi-estimate-scg-taxonomy -c Sample_01.db --metagenome-mode --tree-output --tree-output-level t_phylum
Contigs DB ...................................: Sample_01.db
Metagenome mode ..............................: True
(...)

Taxa in metagenome "Sample_01"
===============================================

All Ribosomal_S11 copies (96)
├── Bacteria (94)
│   ├── Campylobacterota (36)
│   ├── Desulfobacterota (16)
│   ├── Bacteroidota (13)
│   ├── Bacillota_A (8)
│   ├── Pseudomonadota (7)
│   ├── Actinomycetota (2)
│   ├── Desulfobacterota_E (2)
│   ├── Krumholzibacteriota (2)
│   ├── Patescibacteria (2)
│   ├── Acidobacteriota (1)
│   ├── Desulfobacterota_F (1)
│   ├── Fermentibacterota (1)
│   ├── KSB1 (1)
│   ├── Spirochaetota (1)
│   └── WOR-3 (1)
└── Archaea (2)
    └── Halobacteriota (2)
```

And of course all these look much better in the terminal:

<img width="367" height="535" alt="image" src="https://github.com/user-attachments/assets/362ec540-e4e2-4a16-8861-8ae4e3e3d19a" />

It also works with coverages, but it is quite rudimentary at this point and I wish to make it much fancier. Plus, the organization have no phylogenetic meaning or order ... but it COULD have both since anvi'o could has copy of GTDB global tree wink wink. LATER MABBE.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c86ec10c72f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.