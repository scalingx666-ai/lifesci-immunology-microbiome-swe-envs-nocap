# Issue

**Title:** add check for valid bins before DAS_Tool

## Description

Users report workflow crashing during `DAS_Tool` step. This could be caused by several issues. One cause is a poor assembly, in which no bins are produced by MetaBat2. 

The new rule `CheckForBins` evaluates the bins that are supplied to `DAS_Tool`. In cases where no bins were produced by any strategy, the step will throw an error (breaking the workflow), and the problem is described in the associated log file called `logs/SAMPLE.CheckForBins.log`.

Other cases include only circular bins may be produced. If these are plasmid or viral, `DAS_Tool` will fail. A warning should be visible in `logs/SAMPLE.CheckForBins.log` describing this bin pattern. In this case, the sample should be excluded.

There are other cases of unexpected bin behavior which will also be documented in `logs/SAMPLE.CheckForBins.log`. The `CheckForBins` rule will provide an easier way to distinguish bad assemblies from other technical problems in the software tools across various rules.

The `--score_threshold` flag of `DAS_Tool` is now accessible through the `config.yaml` file. The default is set to `0.2`. This value should always be set below the minimum completeness score in GTDB-Tk, where 0.2 = 20%.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c01cadf4a2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.