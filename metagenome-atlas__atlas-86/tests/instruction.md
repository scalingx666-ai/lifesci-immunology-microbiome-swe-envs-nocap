# Issue

**Title:** Update doc

## Description

I realized that much of the documentation is an detailed description of the parameters in the config file. 

I thought it would be great to have as much explanation as necessary as comments in the config file itself. This facilitates the understanding of the values in the config file and avoids that the user has always to consult the doc. 

I managed to do this using the `ruemel.yamel` instead of the `pyyaml` module. 

Now `atlas make-config` reads the file atlas/template_config.yaml and dumps un updated version of it. Admit is looks nice!

I also removed some config values which I think the default user doesn't need to know. But this is based on my estimation. 

I see that this consist in a rather big change, but increases the user-friendliness I hope.

I tested the command on the example data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a65bc517fb67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.