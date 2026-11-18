# Issue

**Title:** Remove invalid $PnE output

## Description

From the FCS3.1 spec:

> $PnE
> If the floating point data type is used (either $DATATYPE/F/ or $DATATYPE/D/), then all parameters shall be stored as linear with $PnE/0,0/.

and

> $DATATYPE
> Note that $PnE/0,0/ shall be used for all parameters if $DATATYPE/F/ is used.

The part of the spec that talks about invalid `$PnE` values is providing recommendations to file readers. Writers should just not make invalid files.

I made this a subclassed warning so it can easily be silenced by users, but could just make it silently ignored also.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8689ef05d325`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.