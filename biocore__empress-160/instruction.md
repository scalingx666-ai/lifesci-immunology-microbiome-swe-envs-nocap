# Issue

**Title:** Merge pull request #30 from kwcantrell/node-hover

## Description

Node hover

A couple this to note for this PR. 
Currently, only nodes with ids in the newick tree will get a visible nodes associated with them. However, you can still select nodes that do not have a visible node as seen here.
![nodes](https://user-images.githubusercontent.com/28127694/80971323-70e5a180-8dd1-11ea-8ba8-44686140109c.png)

selecting none visible node:
![select](https://user-images.githubusercontent.com/28127694/80971332-7511bf00-8dd1-11ea-84d5-db6cf4101393.png)

As you can see from the image above, I assign a generic name to all unnamed nodes (i.e. EmpressNodei) and the default behavior is to display this id. For unnamed nodes, would it be better to hide the id or show a blank?

@fedarko, what version of the js lint are you using? I pull the most recent master branch but it appears we are still using different versions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e9105fadc84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.