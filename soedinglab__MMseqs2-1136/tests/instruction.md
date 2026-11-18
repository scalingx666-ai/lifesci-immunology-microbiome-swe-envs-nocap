# Issue

**Title:** Fix full-byte substitution matrix indexing

## Description

## Summary

This is a extra hardening over #1132 .

This PR makes substitution-matrix lookup tables cover the complete unsigned-byte range and prevents signed `char` values from being used as negative array indexes.

It also includes two small portability fixes discovered while validating the change.

## Problem

The ASCII substitution matrix and `aa2num` mappings used `UCHAR_MAX` as an exclusive upper bound. Because `UCHAR_MAX` is itself a valid byte value, this omitted `0xFF` from the allocated and initialized ranges.

Additionally, several scoring paths converted sequence characters directly to `int`. On platforms where `char` is signed, bytes above `0x7F` could become negative indexes and cause out-of-bounds access.

Character classification and conversion functions such as `isalpha` and `toupper` also require their input to be representable as `unsigned char` or `EOF`.

## Changes

- Allocate and initialize `aa2num` for every value from `0` through `UCHAR_MAX`.
- Expand the fast substitution matrix to cover the complete unsigned-byte range.
- Update nucleotide, amino-acid, and reduced-alphabet mapping loops to include `UCHAR_MAX`.
- Convert raw sequence bytes to `unsigned char` before matrix indexing.
- Pass character-classification inputs through `unsigned char`.
- Preserve the existing behavior of mapping unknown byte values to `X`.
- Add the missing `<sstream>` include in the search workflow.
- Mark the file descriptor unused on platforms without `posix_fadvise`.

## Validation

- Built the `mmseqs` target successfully in the debug configuration.
- Validated the complete byte range, including `0x80` and `0xFF`, under AddressSanitizer using a temporary regression harness.
- Ran the existing reduced-matrix test under AddressSanitizer.
- Verified the patch with `git diff --check`.

A permanent regression test is intentionally deferred until it can be integrated with an appropriate test framework.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d401e78c2d18`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.