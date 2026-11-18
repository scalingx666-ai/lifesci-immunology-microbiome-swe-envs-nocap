# Issue

**Title:** Add JS linting/style-checking; add contributing info; various JS style/code tweaks

## Description

As discussed over email between @kwcantrell, @ElDeveloper, and myself:

- Adds a lot of `make` targets for conveniently running style-checking, auto-formatting, etc.
- Run linting/stylechecking for JS code on Travis using jshint and prettier, respectively
- Add a `make` target (`make githook`) that sets up a pre-commit hook that calls `make stylecheck`. This isn't necessary for development, but it saves some headaches from Travis builds failing at the very end from small style problems.
- Add a `CONTRIBUTING.md` file describing how to use all of the aforementioned `make` targets.
- Various changes to the JS code to shut up jshint. **This still fails**: there's an error [here](https://github.com/fedarko/empress/blob/67d8fdd49efe997ea4ddb18ea3fdc5c5ad190c79/empress/support_files/js/legend.js#L16-L17) where a variable is clobbered where I'm not super sure how to rewrite things. So I'm leaving this as is so that someone who's more familiar with that code can address it.
- Chuck the JS code through prettier (using `make jsstyle`) to autoformat it. It should look somewhat more consistent, now.

(The final two bullet points are responsible for most of the changes in this PR.)

Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9e9ab870c87`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.