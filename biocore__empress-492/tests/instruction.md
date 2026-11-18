# Issue

**Title:** Tree controller

## Description

This PR implements a new object TreeController that will allow empress to support dynamic shearing based on feature metadata or even sample metadata. TreeController will shear the tree based on a set of tip names (based on https://github.com/wasade/improved-octo-waddle/blob/0e9e75b77238acda6752f59d940620f89607ba6b/bp/_bp.pyx#L732). Also, to make integration of TreeController as seamless as possible, all input and output of TreeController will be w.r.t the original tree. In other words empress.js will not know if a tree has been sheared. Instead, TreeController will internally convert its input from the original tree to the sheared tree and back. This makes handling the metadata A LOT easier since empress indexes metadata using a nodes post-order position (w.r.t the non-sheared tree). 

In addition, TreeController introduces iterators for the post-order and in-order traversals (now we no longer need to do `for (i=1; i < this.tree.size; i++)` to perform post-order traversal. Instead, we simply do `for(node of this.tree.postorderTraversal())`)

I've gone through a lot of different iterations of this PR so I am not sure how simple this final product turned out.  So we can also setup a meeting if it makes reviewing this PR easier. :upside_down_face:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c00c3f9f36bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.