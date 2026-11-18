# Issue

**Title:** Fixed sample ID list bug

## Description

Addressed #163, thank @ProsperP for noting this.

Now the following command would work:

```bash
woltka classify -i input_dir -s metadata.tsv ... -o output.biom
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41bd5d61b53e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.