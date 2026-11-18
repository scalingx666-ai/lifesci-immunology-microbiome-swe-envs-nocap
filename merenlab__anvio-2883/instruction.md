# Issue

**Title:** Write llms-full.txt along with the help pages

## Description

This is a , and a first go at the `llms.txt` idea @meren mentioned at the end of #2881.

`anvi-script-gen-help-pages` now also writes an `llms-full.txt` next to the help pages. It's made by a new `LLMsTextRenderer` in `anvio/docs/export.py`, which, just like `HelpPagesRenderer`, only reads the `DocumentationData`. Since anvio.org's nightly sync already runs `anvi-script-gen-help-pages -o help/main`, the file should show up at https://anvio.org/help/main/llms-full.txt once this is merged, without any changes on the anvio.org side.

The file is one big Markdown document. After a short header with the anvi'o version, every workflow (6), program (177), and artifact (162) gets its own section titled `## <name> (<kind>)`. Each section starts with a short list of the useful metadata (URL, description, what it requires and provides, tags, authors, and so on), followed by the Markdown we wrote for it. Artifacts also list the programs that require, provide, or can use them, so you can go from an artifact to the programs around it without leaving the section. The only thing I change in the authored Markdown is heading levels, so that every section's own headings start at `###` no matter how the original file was written. Code blocks are left alone.

Why bother: I've been using this file to back a small MCP server that does semantic search over the docs. On a set of anvi'o planning questions, Claude Haiku went from 31/51 to 45/51 once it could search the docs, and on questions about things that are new in v9-dev it went from 0/30 to 27/30 (without the docs it mostly made up program names). Bigger models gain less on the general questions, but they are just as lost on the new stuff. Having the file on anvio.org means the server can refresh itself every day instead of me feeding it by hand.

A few caveats:

- There are no command line parameters in here, and that's up for debate. First of all, I realize the hypocrisy of calling if `llms-full.txt` when it doesnt include everything. But I primarily imagine this text corpus being used to search and retrieve program documentation, descriptions, and examples. It is my personal ideal that agents should learn about CLI args in a more structured manner, rather than straight text. However, I can concede on this front. We could also easily export two different text files.
- Other than the heading levels, the Markdown is exactly as written, so our own markup shows up raw (`%(anvi-profile)s` style links appear 788 times and `{{ codestart }}` blocks 722 times). Models don't seem to mind, but we could render those into plain Markdown at some point if we want a cleaner file.
- It's about 1.8 MB, so roughly 450k tokens. That's too big to paste into a chat in one go; it's meant to be split into chunks and searched. The llms.txt convention also has a short `llms.txt` index file that points to everything, which I didn't add here.
- Only `help/main` gets the file. The older version folders on anvio.org won't have one unless we regenerate them.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99be594ec8cc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.