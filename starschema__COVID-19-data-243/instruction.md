# Issue

**Title:** Enh/history

## Description

Execution flow rewrite (`dags/covid_etl_dag.py`):
Added` all_*.sql` files to trigger SQL file execution under the `snowflake/sql`.

With the rewrite, the execution steps are modified by running SQL scripts located in the `snowflake/sql` directory (by creating separate tasks for each script and executing them in parallel). Now each SQL file matching the name `snowflake/sql/<table name>*.sql` name run after the table load along with all the files matching the name `snowflake/sql/all_*.sql`. Note, that every `all_*.sql` script runs after every table load.

Added the SQL script parameter `TableName` to the executor task. Using the `{{ TableName }} `parameter in the scripts referencing the actual table.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a066ed694493`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.