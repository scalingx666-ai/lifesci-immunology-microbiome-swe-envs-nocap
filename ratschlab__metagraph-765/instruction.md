# Issue

**Title:** Avoid repeated-row expansion before ranking search results

## Description

Repetitive queries map the same annotation coordinates at many query positions. Searches by sequence record also retain values for records that will not be returned.

Decode distinct rows in blocks and count repeated rows with their query multiplicity. Expand their coordinates, signatures and counts only for returned records. Without a record mapping, reuse each decoded row at its query positions.

Once stored runs exceed 16 MiB, discard values for records that cannot reach the match threshold or requested top results. If too many candidates still retain substantial values, keep counts and read the selected records’ values again after ranking. Returned results and temporary decoding buffers can exceed this threshold. A matched 4–256 MiB sweep selected 16 MiB: smaller thresholds caused additional decoding on the ordinary-query fixtures, while larger thresholds increased intermediate memory on the distinct-row fixture.

Sort coordinate values once and release their scratch buffer between records. On the three-record poly-A fixture returning all records, GCC 13.3 Release runs used 7.36–7.37 GiB and took 52–54 s, versus the same memory and 74 s on ec3969b7 (`-p 1`). An ordinary 5 kbp query remained slightly slower: median 2.49 s versus 2.44 s in these runs.

The integration query includes one unique k-mer so parallel annotation cannot change the selected column. Its 512 MiB limit is unchanged.

🤖 Developed with Claude Code and Codex.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8942c44dc231`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.