# Issue

**Title:** made map as rank default

## Description

Originally, the flag `--map-as-rank` tells the program to extract a rank name from each mapping file name. For example:

<pre><code>woltka classify \
  -i indir \
  --coords coords.txt \
  --map wol-to-uniref.map \
  --map uniref-to-metacyc.map \
  <b>--map-as-rank</b> \
  --rank uniref,metacyc \
  -o outdir</pre></code>

However, this extra line of command is bit counter-intuitive and hard to remember.

The current PR made this automatic, so that the user can save one parameter from their command. A large number of example commands in the documentation are therefore one-line shorter.

The rule is: When there are only mapping files (`-m`) but no other hierarchy files (`--nodes`, `--lineage`, `--newick` etc.), this function will be turned on (i.e., the program will extract a rank name from each mapping file name) automatically.

Meanwhile, the user can use `--map-as-rank` or `--map-no-rank` to force this function to be on or off.

The reason this function is not always on is because the following scenario is also common:

```bash
woltka classify \
  -i indir \
  --map taxid.map \
  --nodes nodes.dmp \
  --names names.dmp \
  -o free.tsv
```

This will perform a free-rank classification (i.e., each query will be assigned to the lowest rank where all its subjects agree with). However, "**taxid**" should not be considered a rank. In scenarios where other hierarchy files are used, the simple mapping files typically serve as bridges rather than end goals.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac0823f6387d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.