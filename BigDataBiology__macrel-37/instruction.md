# Issue

**Title:** add models trained with pep. with 50 res. or less

## Description

# AMP (unbalanced training) CLASSIFIER 
Accuracy: 0.921
MCC: 0.74

Confusion matrix:
[[812  77], [  4 128]]

              precision    recall  f1-score   support

         AMP      0.995     0.913     0.952       889
        NAMP      0.624     0.970     0.760       132

    accuracy                          0.921      1021
   macro avg      0.810     0.942     0.856      1021
weighted avg      0.947     0.921     0.928      1021

# AMP (benchmark training) CLASSIFIER 
Accuracy: 0.946
MCC: 0.766

Confusion matrix:
[[858  31], [ 24 108]]

              precision    recall  f1-score   support

         AMP      0.973     0.965     0.969       889
        NAMP      0.777     0.818     0.797       132

    accuracy                          0.946      1021
   macro avg      0.875     0.892     0.883      1021
weighted avg      0.947     0.946     0.947      1021

# Hemo CLASSIFIER 
Accuracy: 0.945
MCC: 0.889

Confusion matrix:
[[104   6]
 [  6 101]]

              precision    recall  f1-score   support

        Hemo      0.945     0.945     0.945       110
     NonHemo      0.944     0.944     0.944       107

    accuracy                          0.945       217
   macro avg      0.945     0.945     0.945       217
weighted avg      0.945     0.945     0.945       217

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72fb92d820be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.