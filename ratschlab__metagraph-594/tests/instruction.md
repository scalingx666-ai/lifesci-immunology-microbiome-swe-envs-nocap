# Issue

**Title:** Upgrade sshash to v5.0.0 with API compatibility changes

## Description

Upgraded sshash from previous version to v5.0.0 (upstream master). This required significant API adaptation due to breaking changes.

API changes handled:
1. dictionary now requires two template parameters: dictionary<Kmer, Offsets>
   - Added sshash::decoded_offsets as second parameter throughout

2. Method renames:
   - size() → num_kmers()
   - lookup_advanced() → lookup()

3. streaming_query template parameter changed:
   - Was: streaming_query<kmer_t, bool>
   - Now: streaming_query<Dict, bool> (takes dictionary type)

4. Use dictionary::kmer_type instead of template_parameter extraction
   - Replaced get_kmer_t helper with decltype(dict)::kmer_type
   - Cleaner approach using built-in typedef from sshash

Code quality improvements:
- Removed template_parameter helper struct and get_kmer_t alias
- Simplified kmer type extraction in lambda expressions

Submodule update:
- Updated external-libraries/sshash to merge-upstream-master-with-metagraph-compatibility
- Includes cityhash namespace wrapping and accessor methods
- Includes pthash fix for multiple definition errors

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf7b1db6447c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.