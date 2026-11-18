# Issue

**Title:** enzymes-txt support for anvi-draw-kegg-pathways

## Description

This PR adds `enzymes-txt` support for `anvi-reaction-network` and `anvi-draw-kegg-pathways`, which allows the programs to work without a contigs-db. 

I used a simple [test-enzymes.txt](https://github.com/user-attachments/files/28643487/test-enzymes.txt), which looked like this,

|**`gene_id`**|**`enzyme_accession`**|**`source`**|
|:--|:--|:--|
|gene_001|K00844|KOfam|
|gene_002|K01810|KOfam|
|gene_003|K00850|KOfam|
|gene_004|K01623|KOfam|
|gene_005|K00134|KOfam|
|gene_006|K00927|KOfam|
|gene_007|K01834|KOfam|
|gene_008|K01689|KOfam|
|gene_009|K00873|KOfam|
|gene_010|K00024|KOfam|
|gene_011|K01647|KOfam|
|gene_012|K01681|KOfam|
|gene_013|K00031|KOfam|
|gene_014|K00030|KOfam|
|gene_015|K00164|KOfam|
|gene_016|K00658|KOfam|
|gene_017|K01902|KOfam|
|gene_018|K01903|KOfam|
|gene_019|K00382|KOfam|
|gene_020|K01899|KOfam|

to test the new parameters. Using this test file I got the necessary JSON output first:

```
anvi-reaction-network --enzymes-txt test-enzymes.txt \
                      --output-json test-network.json
```

And then passed it to `anvi-draw-kegg-pathways`:

```
anvi-draw-kegg-pathways --reaction-network-json test-network.json \
                        --ko \
                        -o test-pathway-maps/
```

And got all the maps expected given the enzymes mentioned in the test file (that touched on Glycolysis, TCA cycle, Carbon metabolism etc).

Here are some of the enzymes in this file in the context of Glycolisis:

<img  alt="image" src="https://github.com/user-attachments/assets/aeffca1a-9e2d-47eb-83eb-497b4bff5bc7" />

---

And here is an example of those in TCA cycle:

<img alt="image" src="https://github.com/user-attachments/assets/a8c66c36-e2a9-4c5a-8045-607f4e786aa9" />

This finally implements a feature request by @ivagljiva (#2487), and closes an issue (#2705), addressing @rpeguil's need.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0de7825471d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.