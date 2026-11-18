# Issue

**Title:** Drop db_params patterns for bracken and kmcp

## Description

<!--
# nf-core/taxprofiler pull request

Many thanks for contributing to nf-core/taxprofiler!

Please fill in the appropriate checklist below (delete whatever is not relevant).
These are the most common things requested on pull requests (PRs).

Remember that PRs should be made against the dev branch, unless you're preparing a pipeline release.

Learn more about contributing: [CONTRIBUTING.md](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
-->

Fix the issue #475 

The original definitions of db_params of `bracken` and `kmcp` in `db_check.nf``
```
    if ( row.tool == 'bracken' && row.db_params && !row.db_params.contains(";") )  error("[nf-core/taxprofiler] ERROR: Invalid database db_params entry. Bracken requires a semi-colon if passing parameter. Error in: ${row}")
    if ( row.tool == 'kmcp' && row.db_params && row.db_params.matches(".*;\$"))  error ("[nf-core/taxprofiler] ERROR: Invalid database db_params entry. KMCP only requires a semi-colon if passing arguments to KMCP profile, in cases of which the arguments should go after the semi-colon. Error in: ${row}")

```

The database.csv used in this test:

```
tool,db_name,db_params,db_path
bracken,db1,;-r 150,https://github.com/nf-core/test-datasets/raw/taxprofiler/data/database/bracken/testdb-bracken.tar.gz
kraken2,db2,--quick,https://github.com/nf-core/test-datasets/raw/taxprofiler/data/database/kraken2/testdb-kraken2.tar.gz
kmcp,db1,;\$--min-kmers 30;\$--min-query-cov 0.5,https://github.com/nf-core/test-datasets/raw/taxprofiler/data/database/kmcp/test-db-kmcp.tar.gz

```

The Bracken output files in this test:
![image](https://github.com/nf-core/taxprofiler/assets/64467552/3803e051-47b2-44f9-86cb-7ee8a25d5780)

kmcp output files in this test:
![image](https://github.com/nf-core/taxprofiler/assets/64467552/ef8f287b-9111-447b-a129-6c762b2a3a6c)


## PR checklist


- [ ] This comment contains a description of changes (with reason).
- [ ] If you've fixed a bug or added code that should be tested, add tests!
- [ ] If you've added a new tool - have you followed the pipeline conventions in the [contribution docs](https://github.com/nf-core/taxprofiler/tree/master/.github/CONTRIBUTING.md)
- [ ] If necessary, also make a PR on the nf-core/taxprofiler _branch_ on the [nf-core/test-datasets](https://github.com/nf-core/test-datasets) repository.
- [ ] Make sure your code lints (`nf-core lint`).
- [ ] Ensure the test suite passes (`nf-test test main.nf.test -profile test,docker`).
- [ ] Check for unexpected warnings in debug mode (`nextflow run . -profile debug,test,docker --outdir <OUTDIR>`).
- [ ] Usage Documentation in `docs/usage.md` is updated.
- [ ] Output Documentation in `docs/output.md` is updated.
- [ ] `CHANGELOG.md` is updated.
- [ ] `README.md` is updated (including new tool citations and authors/contributors).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7cd983c70c39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.