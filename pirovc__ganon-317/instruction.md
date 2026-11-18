# Issue

**Title:** Feature/tax stats

## Description

Generate a taxonomic statistics by rank when creating reports with content reported:

```
            unique     shared     children   total      
   root     0%         0%         39.28%     39.28%     
   domain   0%         0.3192%    38.96%     39.28%     
   phylum   0%         0.5191%    38.37%     38.89%     
   class    0%         0.4569%    37.9%      38.36%     
   order    0%         0.4658%    37.44%     37.91%     
   family   0%         1.028%     36.36%     37.39%     
   genus    0%         4.243%     32.17%     36.41%     
   species  30.58%     0%         0%         30.58%     
   assembly 0%         0%         0%         0%   
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35c031845c99`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.