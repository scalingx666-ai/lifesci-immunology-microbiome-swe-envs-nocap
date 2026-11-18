# Issue

**Title:** Update RDA/CCA functions

## Description

Hello,

this PR is partly overlapping with this one: 

I completely rewrote *RDA and *CCA functions. That is for easier maintenance and to make the code simpler. I have been looking this file a while and thought that it is far more complex than it could be.

Keypoints:

1.

RDA and CCA functions use same code. The interface to vegan is similar in both methods, so it is easier for us to use same code.

2.

It was little but unclear what was the output as we use different naming scheme than vegan. Now we use directly the output from vegan. Moreover, scores parameter was kind of useless, so it is now removed (not deprecated since I think there was no clear use)


Thing to do:

1. Update documentation

a)

Clearly state that these a wrappers for vegan::cca and vegan::dbrda.

b)

Clearly state that the output matrix is site scores. The attributes include the output from vegan::scores, eigenvalues, the object and possible significance testing results.

2.Check that scores parameter is removed from test file.

3. Fix plotRDA and plotLoadings

They are expecting that attr(mat, "rda") includes the object. However, now it is in attr(mat, "obj") (Check if the object is found from "obj", "rda" or "cca" --> no visible change to user)

User probably might want to plot either biplot values or species scores. We could have a parameter for this. Take into account that in PCA the "loadings" are in "rotation" attribute.

3 Check if scater package have a method for plotting eigenvalues.

4 Run BiocCheck and fix everything related to this file

@Daenarys8 Do you have time to implement these?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1923e870e240`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.