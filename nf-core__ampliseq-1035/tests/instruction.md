# Issue

**Title:** Update ITSxRust to 0.3.0

## Description

<html><head></head><body><p>Bumps ITSxRust from 0.2.2 to 0.3.0 in <code>modules/local/itsxrust_cutasv.nf</code>. Three lines: the conda pin and the two container URLs (<code>0.3.0--h70df5c0_0</code>).</p>
<h3>Why</h3>
<p>The main change upstream is a memory fix. ITSxRust invokes <code>nhmmer</code> as a subprocess and parses its <code>--tblout</code> output, but the wrapper was also capturing <code>nhmmer</code>'s human-readable report into memory and discarding it. On a 230 Mbp Nanopore ITS dataset that accounted for roughly 6 GB of a 7 GB peak.</p>

  | 0.2.2 | 0.3.0
-- | -- | --
Peak RSS, 108,000 reads / 230 Mbp | 7.07 GB | 1.10 GB
Peak RSS, 54,659 reads / 45.9 Mbp | 3.76 GB | 0.52 GB
Wall time | unchanged | unchanged


<p>Peak memory now scales at roughly 10 kB per input read and is independent of read length, so it can be estimated from read count in advance. That seemed worth bumping for, given ampliseq is often run on shared schedulers.</p>
<h3>Verification</h3>
<p>Extraction counts are <strong>identical between 0.2.2 and 0.3.0 in every field</strong>, checked on two datasets (54,659 and 108,000 reads): kept, full-chain, partial, skipped, and per-region ITS1/ITS2/full ITS counts all match exactly. The captured stream was never read, so nothing downstream changes and no snapshots need updating.</p>
<h3>Also in 0.3.0, not used by this module</h3>
<ul>
<li><code>--region ssu</code> and <code>--region lsu</code> to export the flanking ribosomal genes</li>
<li><code>--plain-ids</code> to omit the coordinate suffix from output headers</li>
<li>a warning when supplied HMM profile names don't map to a recognised anchor type, rather than silently under-detecting anchors</li>
</ul>
<p>The module's invocation is unchanged, so none of these alter ampliseq behaviour. <code>--preset</code> selection via <code>params.sequencing_type</code> in <code>conf/modules.config</code> is untouched.</p>
<h3>Notes</h3>
<ul>
<li>CHANGELOG entry added under <code>Dependencies</code> for 3.0.0dev, with the version table.</li>
<li>No parameter, schema or documentation changes.</li>
<li>Disclosure: I maintain ITSxRust and added the module in #957 / #979.</li>
</ul>
<p>Release notes: https://github.com/ayobi/ITSxRust/blob/main/CHANGELOG.md</p>
<h2>PR checklist</h2>
<ul>
<li>[x] This comment contains a description of changes (with reason).</li>
<li>[ ] Make sure your code lints (<code>nf-core pipelines lint</code>) — deferred to CI; local <code>nf-core</code> install has a pydantic v1/v2 conflict.</li>
<li>[ ] Ensure the test suite passes — deferred to CI. The default <code>test</code> profile does not exercise ITSxRust, which requires <code>its_extractor = 'itsxrust'</code> (<code>test_pacbio_its</code>).</li>
<li>[x] <code>CHANGELOG.md</code> is updated.</li>
</ul></body></html>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8925757ecb43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.