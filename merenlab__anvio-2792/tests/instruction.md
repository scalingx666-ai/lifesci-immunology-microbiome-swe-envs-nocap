# Issue

**Title:** Index pooling rather than naive rescanning

## Description

I ran into a significant performance issue, and this PR addresses that. Pinging @ahenoch since he may want to be aware of this.

Something that worked on 3,012 loci stopped working when I removed 5 of those loci that made the graph complicated. My removal of those genomes dramatically simplified the graph, but actually in this case it was worse for the algorithm, so it took hours and hours for something that should have taken seconds. And it was then I realized we had a N*log(N^4) scale problem at our hands.

Buckle up for fun. While building the pangenome graph, especially when we are dealing with edges, the inner take_bucket() scans the ranked edge pool to make decisions. But every time it runs into a new edge, it scans the bucket from position zero, and because it skips (but never consumes) edges whose both endpoint contigs are still off the graph, the same tens of thousands of head rows get re-examined hundreds of thousands of times for a relatively small set of genomes which turns into hundreds of millions of comparison, which turns a few seconds work into hours of wait.

This solution indexes the pool instead of rescanning it. It has map to connect lines to row positions, a min-heap of the positions that touch the current frontier (so edges still pop in exact ranking order), and tombstones in place of list.pop(idx). It does not change anything, but comes with about 2 orders of magnitude speed difference in pangenome graphs with MANY overlapping edges.

There is a much deeper issue here that I didn't want to address. In my case with these loci, the pool holds hundreds of thousands of edges to build a 100-node graph (literally).. The pool grows with the square of the genome count while the answer stays tiny, and those edges carry only a few distinct ranking scores with tens of thousands of them remain tied. Collapsing redundant within-gene-cluster edges before fusion, AND adding tie-breaking resolution to the ranking would shrink the work at the source and, just as importantly, stop tiny input changes like removing a few genomes from the analysis to silently reshuffle which edges get seen first.

But this is such a niche problem, I don't think we need to go that deep into the realm of kitchen sinks (this already is a bit of a kitchen sink at this stage as it is). This change will likely be enough for over 99.99% of the applications of this algorithm.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d61443a01f11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.