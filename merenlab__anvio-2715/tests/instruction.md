# Issue

**Title:** anvi-export-pan-subgraph += --region-id

## Description

`anvi-export-pan-subgraph` is an anvi'o program that exports genomic loci from every single contigs-db in a given pangenome-graph that is in between two user-provided nodes in a pangenome graph. The user had to identify two core SynGCs, and run it from the command line like this to get all the contigs-db files from from individual genomes:

```
anvi-export-pan-subgraph -e external-genomes.txt \
                         -p UNDATIPELAGIBACTER-PAN-GRAPH.db \
                         --graph-nodes GC_00000111_1, GC_00001142_1 \
                         -o REGION-32
```

The resulting directory then would look something like this:

```
ls REGION-32

HIMB122-PROFILE  HIMB1506-PROFILE HIMB1552-PROFILE HIMB1593-PROFILE HIMB1641-PROFILE HIMB1723-PROFILE
HIMB122.db       HIMB1506.db      HIMB1552.db      HIMB1593.db      HIMB1641.db      HIMB1723.db
HIMB140-PROFILE  HIMB1507-PROFILE HIMB1556-PROFILE HIMB1597-PROFILE HIMB1662-PROFILE HIMB1758-PROFILE
HIMB140.db       HIMB1507.db      HIMB1556.db      HIMB1597.db      HIMB1662.db      HIMB1758.db
HIMB1488-PROFILE HIMB1513-PROFILE HIMB1559-PROFILE HIMB1611-PROFILE HIMB1685-PROFILE HIMB1765-PROFILE
HIMB1488.db      HIMB1513.db      HIMB1559.db      HIMB1611.db      HIMB1685.db      HIMB1765.db
HIMB1491-PROFILE HIMB1518-PROFILE HIMB1573-PROFILE HIMB1631-PROFILE HIMB1701-PROFILE HIMB1770-PROFILE
HIMB1491.db      HIMB1518.db      HIMB1573.db      HIMB1631.db      HIMB1701.db      HIMB1770.db
HIMB1493-PROFILE HIMB1526-PROFILE HIMB1577-PROFILE HIMB1636-PROFILE HIMB1702-PROFILE
HIMB1493.db      HIMB1526.db      HIMB1577.db      HIMB1636.db      HIMB1702.db
```

But thanks to @ahenoch's thorough and thoughtful conduct, anvi'o already assigns 'region' ids to a given pangraph like this:

<img width="669" height="581" alt="image" src="https://github.com/user-attachments/assets/da34295e-3882-4f0c-831b-edf581ce5c42" />

And since `pan-graph-db` knows exactly how these regions are associated with nodes on the graph, it can find the flanking nodes itself. So, this PR takes advantage of that fact and adds **a new parameter for `anvi-export-pan-subgraph` that makes it much more straightforward to get contigs-db files for pan subgraphs using a known region id**:

```
anvi-export-pan-subgraph -e external-genomes.txt \
                         -p UNDATIPELAGIBACTER-PAN-GRAPH.db \
                         --region-id 32 \
                         -o REGION-32
```

It works like a charm. There is a but of nuance in its inner workings when the region id resolves to a VR rather than a BR, but the program lets the user know about what is going on in that case with an anvi'onic`*` warning:

```
anvi-export-pan-subgraph -e external-genomes.txt \
                         -p UNDATIPELAGIBACTER-PAN-GRAPH.db \
                         --region-id 32 \
                         -o REGION-32

WARNING
==============================================================
The pan database is being initialized without a genomes storage.

Pan Graph DB ................................................: Initialized: UNDATIPELAGIBACTER-PAN-GRAPH.db (v. 21)

WARNING
===============================================
The region ID 32 corresponds to a variable region. Variable region nodes are not
necessarily present in all genomes, so anvi'o will instead use the closest
flanking backbone nodes: 'GC_00000111_1' on the left and 'GC_00001142_1' on the
right. The exported loci will include the variable region content plus at least
two extra genes from the flanking backbone regions (one on each side). In cases
where the closest backbone node adjacent to the variable region is a non-coding
gene (such as a tRNA or rRNA), anvi'o steps past it to the next coding backbone
node; which means that non-coding gene also ends up inside the exported locus,
giving you more than two extra genes. If you end up analyzing the conservancy of
genes in variable regions you MUST consider this to avoid misinterpretations.

Region ID ....................................: 32 (variable)
Pangenome graph database .....................: UNDATIPELAGIBACTER
Pan graph database ...........................: UNDATIPELAGIBACTER-PAN-GRAPH.db
Nodes to export ..............................: GC_00000111_1, GC_00001142_1
Loci .........................................:
    - 115 to 192 (77 genes) for HIMB122
    - 117 to 187 (70 genes) for HIMB140
    - 116 to 206 (90 genes) for HIMB1488
    - 126 to 179 (53 genes) for HIMB1491
    - 129 to 168 (39 genes) for HIMB1493
    - 150 to 227 (77 genes) for HIMB1506
    - 116 to 169 (53 genes) for HIMB1507
    - 148 to 197 (49 genes) for HIMB1513
    - 117 to 169 (52 genes) for HIMB1518
    - 117 to 191 (74 genes) for HIMB1526
    - 117 to 191 (74 genes) for HIMB1552
    - 116 to 190 (74 genes) for HIMB1556
    - 166 to 233 (67 genes) for HIMB1559
    - 168 to 210 (42 genes) for HIMB1573
    - 116 to 173 (57 genes) for HIMB1577
    - 126 to 190 (64 genes) for HIMB1593
    - 166 to 233 (67 genes) for HIMB1597
    - 122 to 174 (52 genes) for HIMB1611
    - 117 to 174 (57 genes) for HIMB1631
    - 116 to 179 (63 genes) for HIMB1636
    - 117 to 180 (63 genes) for HIMB1641
    - 116 to 174 (58 genes) for HIMB1662
    - 117 to 183 (66 genes) for HIMB1685
    - 117 to 196 (79 genes) for HIMB1701
    - 117 to 179 (62 genes) for HIMB1702
    - 117 to 183 (66 genes) for HIMB1723
    - 122 to 173 (51 genes) for HIMB1758
    - 119 to 156 (37 genes) for HIMB1765
    - 129 to 181 (52 genes) for HIMB1770

✓ export_pan_subgraph.py took 0:00:08.386820
```

---

`*` **anvi'onic** _(adj.)_ -- of code, design, or solutions: exhibiting the qualities valued by the anvi'o project, including but not limited to design elegance, code economy, and a stern _researcher-first_ attitude with transparency of decisions and communicating their implications on downstream science. Not to be confused with anvi'an (n./adj.), which denotes a member of the anvi'o community rather than a property of their work. _Usage note:_ The term is mostly aspirational. A contribution described as _anvi'onic_ does not necessarily mean it has achieved these qualities in full, but it would merely indicate a credible pursuit of them. _Etymology note_: See  where the term was introduced, discussed, and ratified by @ekiefl and @meren, presidents of The Committee on Anvi'an Nomenclature<sup>_[citaton needed]_</sup> (TCOAN (pronounced as too͞-kăn′ (like toucan the bird)).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f39cdc7c096e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.