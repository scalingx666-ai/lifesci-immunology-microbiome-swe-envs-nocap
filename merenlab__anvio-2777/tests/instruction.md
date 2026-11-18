# Issue

**Title:** Contig rotation and reorientation fixies

## Description

This PR introduces some serious changes that make `anvi-reorient-genomes` a better beast.

Here is the explanation for the most critical changes, copy-pasta'd from the docs updated in the PR:

----

(...)

### Why the number of contigs may increase

{:.notice}
TL;DR: A query genome can come out of this program with **more contigs than it went in with**. This is not a bug, and it is not anvi'o being clumsy with your data :) You can always use `--keep-query-contigs-intact` to keep all your contigs intact, but you must read this section first, because if you are using that flag you are trading one problem for another.

Everything this program does (ordering contigs, orienting them, scaffolding them) depends on a single coordinate axis: the reference. In most cases, that axis has a single beginning and a single end. Your query contigs, meanwhile, are linear sequences that know nothing about where the reference happens to begin.

So what happens to a query contig that runs past the beginning or the end of that axis? Say the reference has been rotated so that it starts at the DnaA gene, and one of your query contigs looks like this:

```
        DnaA
         |
         -----------------------------------------------------------
                          reference
xxxxxxxxx---------------------           -----------------
        Contig 1                             Contig 2
```

The `xxxxxxxxx` part of `Contig 1` hangs off the left edge of the reference. Since the reference is circular, that stretch of sequence very likely aligns beautifully to the far *right* end of the reference (the region just *before* DnaA in the actual circular genome). Which means `Contig 1` has *two* places it belongs on the reference axis, at opposite ends of it, and there is no way to write it into a FASTA file in one piece that is honest about both. Written out whole, it would look like this:

```
>Contig_1
xxxxxxxxx---------------------
>Contig_2
-----------------
```

It means every downstream tool would take the first nucleotide of `Contig_1` as the leftmost thing in the genome, even though it belongs at the far right. While identities of the aligned fractions will look great, in its FASTA form, the genome will *not be aligned to the reference*. Rotating the contig here is not a solution either (Meren's note: the author will eat these words as this will be a solution for an entirely different problem we will discuss later in this document). Becasue `Contig_1` is a linear piece of DNA, not a circle, so moving its beginning to its end invents a junction between two stretches of sequence that are not adjacent in the organism.

The only honest option is to cut the contig, which is what anvi'o does by default:

```
DnaA
 |
 -----------------------------------------------------------
                     reference
 ---------------------           ----------------- xxxxxxxxx
 Contig_1_fragment_01             Contig_2         Contig_1_fragment_02
```

%(anvi-reorient-genomes)s will then align each fragment to the reference on their own merit, ordering and orienting them like any other contig, and reporting them individually.

**Anvi'o will never invent sequences and never throws any of them away**. The fragments of a contig will merge into the same contig exactly, so if you concatenate them back together you get your original contig back, nucleotide for nucleotide.

Three things trigger a cut:

* **The contig straddles the position at which the reference begins and ends**, as in the example above. This is extremely common the moment anything is rotated, but it is *not* limited to rotation: if you bring your own reference with `--reference` and it was circularized at a different position than your query genomes were, you will see exactly the same thing.

* **One end of the contig hangs off the beginning or the end of the reference.** That stretch of sequence has nowhere to go on the reference axis, and letting it ride along inside a contig that *is* placed makes it look like it was placed too. It is cut off and reported as an unaligned contig, so you can see it for what it is.

* **The contig closes on itself around the reference.** This is the sneakiest case of all, since such a contig looks perfectly well-behaved: read along it, the reference coordinate marches forward from the very beginning of the reference to its very end, and nothing looks swapped or scrambled. What gives it away is that it skips an enormous stretch of the reference on the way, and that its two ends turn out to be *neighbours* once you stop measuring their distance along the linear reference axis and measure it around the reference instead (see '*Circularly permuted contigs*' below). Written out whole, such a contig goes wherever its largest alignment block belongs, and drags the part of itself that belongs at the very *end* of the genome along with it, past every other contig. So anvi'o cuts it at the stretch it skips, and the two parts go to the two ends of the output file where they belong. Anvi'o will only do this when other contigs of the same genome cover the skipped stretch, since that is the proof that the sequence is present in the query rather than missing from it, and therefore that the junction being cut is an artifact of assembly rather than a deletion worth preserving.

The second one deserves a word of caution, because "has no alignment" is *not* by itself a reason to cut anything. Query genomes are full of variable regions that have no counterpart in the reference, and a contig that sits comfortably inside the reference with an unaligned stretch at one of its ends is just a genome being a genome. So before cutting, anvi'o asks whether there is enough reference left over before the contig's alignment, or after it to accommodate that unaligned sequence. If there is enough reference left over, it would mean that the sequence would not be hanging off anything and anvi'o would leave the poor contig with assumed hypervariability alone and intact. Anvi'o will take out its 8< only when the unaligned stretch is longer than the remaining length of the reference context. Just to put it in different words, a 20,000 nt unaligned tail on a contig that stops 400,000 nt short of the end of the reference is a variable region. But a 20,000 nt unaligned tail on a contig that stops 8 nt short of the end of the reference is dangling and may want to somewhere else.

Anvi'o will not cut a contig into a fragment shorter than `--min-contig-length` (1,000 bp by default). This is what keeps the handful of nucleotides `minimap2` routinely soft-clips off the end of a divergent alignment from being promoted into contigs of their own, and it is also the yardstick for "long compared to the reference remaining": if the part of an unaligned end that genuinely cannot fit on the reference is shorter than this, anvi'o shrugs and keeps the contig whole.

As everything that happens to your contigs/genomes, anvi'o will report every cut on your terminal, naming the contig, where it was cut, why, and where each resulting fragment ended up on the reference for your information:

```
QUERY CONTIGS CUT INTO FRAGMENTS IN BLAH
===============================================
Anvi'o had to cut 1 contig in BLAH into 2 fragments, which means
this genome will have more contigs in the output file than it had
in the input file. (...)
    - 'contig_01' (165,000 nts) was cut into 2 fragments at position 69,844,
      since it straddles the position at which the reference begins and ends:
        > 'contig_01_fragment_01' (69,844 nts) aligns to the reference at
          position 130,157 on the + strand.
        > 'contig_01_fragment_02' (95,156 nts) aligns to the reference at
          position 25 on the + strand.
```

Fragments are numbered along the original contig, from its first nucleotide to its last, so their names tell you how they were related to one another in your input assembly no matter where each of them ends up in the output file. In the example above `contig_01_fragment_02` is written *before* `contig_01_fragment_01` in the output FASTA, because that is where it belongs on the reference.

If you would rather keep your contigs intact (because a downstream tool of yours cannot cope with changing contig names or counts or something) you can always use use `--keep-query-contigs-intact`. In that case no contig will be cut, but you will most likely be doing a mistake unless you really are sure this is the right way to go with your data (in some cases, it will be the right way to go about it). Anvi'o will not pretend otherwise, either: a genome that ends up with a contig that maps to both the beginning and the end of the reference is reported as `NOT TRUSTWORTHY` regardless of how good its alignment statistics look, since its gene order no longer follows the reference (see '*Interpreting trust labels*' under '*Tips, caveats, and runtime*').

### Circularly permuted contigs, or why a contig sometimes looks scrambled

{:.notice}
TL;DR: Sometimes a query contig aligns to the reference in two big pieces whose order is *swapped*, as if half the genome had been rearranged. Usually nothing has been rearranged: the contig was cut out of a cycle in an assembly graph at an arbitrary point. Anvi'o recognizes these and rotates them back into place, and tells you when it does.

Every now and then you will have a contig that will align the reference perfectly, but in a weird way. The reference coordinate will march forward until the end of the contig, and then all of a sudden it will go back, kind of looking like this (notice the middle contig in the reference genome):

![](../../images/anvi-reorient-genomes-circular-permutated-contig-01.png)

Taken at face value, this look like a huge rearrangement (and if that was the case anvi'o would have no business touching it since rearrangements are real differences between genomes). But this one is not since its boundaries are solely determined by the boundaries of the contig. This actually **is an artifact of how the contig came out of the assembler**. Add it to the list of funny things assemblers do.

Here is what is happening here: a contig (as in a fragment of an otherwise circular chromosome) is reported from an assembly graph as a contig due to multiple complications, including unresolvable circularities that form in the construction of the cassembly graph primarily due to biology. In those cases where large circular edges are formed in the assembly graph, the assembly algorithm is literally looking at a circular genome (just sprouting from a braoder circular context like a very big balloon, which, in the example above, represents that middle contig in HIMB1485). So the algorithm cuts the circualr piece and reports a contig. But there are as many possible start positions for that pseudo-circular subgraph as there are nucleotides in that *balloon*. Depending on the assembly algorithm, the reported fragments may end up not starting from where the balloon originally conneced to the broader genomic context. And as a result, against a better reference, the linear form of that fragment as if it was *circularly permutated* which will make the the contig close on itself.

%(anvi-reorient-genomes)s will correct such contigs since they completely violate the synteny of genes in the actual genomic context. But it will require both of these to be correct before touching such a contig:

1. Read along the contig the alignment blocks jump backwards in reference coordinates **exactly once**. Since a rotation of this sort can explain one and only one jump.
2. The reference position where th e**first** block of the candidate contig begins is immediately after where its **last** block ends, within `--min-contig-length` nucleotides. So that the two ends are genuine neighbours, and rotating the contig will not invent any chimeric adjacency that is not already in the sequence (like your assembly algorithm did :') (sad lol)).

That second distance is measured **around** the reference rather than along it, since the sequences these contigs come from are circular and the position at which the reference begins and ends is an arbitrary point on that circle. A contig whose first block begins 6 nts after the beginning of the reference and whose last block ends 7 nts before the end of a 1,453,515 nt reference has its two ends 13 nts apart -- and *not* a megabase apart, which is all a linear axis can see. Getting this wrong is exactly how a contig ends up spanning the whole reference in the output file (which is the third cutting case described under '*Why the number of contigs may increase*' above).

When anvi'o rotates the contig into co-linearity, you will see messages like these in your terminal:

```
CIRCULARLY PERMUTED CONTIGS ROTATED IN HIMB1485
===============================================
Anvi'o rotated 1 contig in 'HIMB1485'. Contigs like these come out of an
assembler having been cut out of a cycle in its assembly graph (...)
    - 'HIMB1485_000000000002' (961,822 nts) was rotated by 527,750 nts, since
      its two ends are 361 nts apart on the reference and it therefore closes
      on itself. It now aligns to the reference in 3 pieces.
```

The contig will keep its name, keeps every one of its nucleotides, and does not become two contigs. Only the point at which it is considered to start has moved.

Here is the demonstration that it works using the example above where one circular rotation of a linear contig (as crazy as it sounds) collapses a contig that (in this particular case) aligned in five scattered blocks into a single one-megabase alignment, changing the reference coverage of the query from 64%% to 94.7%%:

![](../../images/anvi-reorient-genomes-circular-permutated-contig-02.png)

Again, if you would rather this did not happen, `--keep-query-contigs-intact` will stop any rotations of query contigs even if they set themselves on fire.

(...)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a5579f1c1ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.