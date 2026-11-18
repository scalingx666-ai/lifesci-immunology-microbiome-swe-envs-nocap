# Issue

**Title:** modify full_database_download.bash issue66

## Description

From issue: [)
I recently used full_database_download.bash and found an error message below.
full_database_download.bash: 26: full_database_download.bash: source: not found

So, I suggest to fix full_database_download.bash as shown below.

`source "${BASH_SOURCE%/*}/../bash_scripts/lib/common.sh"`
->

```
if [[ -d "${BASH_SOURCE%/*}/../bash_scripts/lib/common.sh" ]]; then
  source "${BASH_SOURCE%/*}/../bash_scripts/lib/common.sh"
else
#assuming that you're running this full_database_download.bash directly ("bash full_database_download.bash")
  source "../bash_scripts/lib/common.sh"
fi
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `248b9c37ce7e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.