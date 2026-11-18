# Issue

**Title:** Revamping `ProgramsVignette` for agentic access

## Description

This PR builds on what @ekiefl started in #2853 to make anvi'o more accessible to agentic coding and workflow building efforts by describing everything anvi'o programs can do as structured data that machines can read, rather than only as prose and terminal output meant for humans, which is how we have been rolling so far but now caving in to empower our agentic users in addition to our human users..

The PR extends the `DocumentationData` class with proper descriptions of all anvi'o program parameters (their flags, help text, defaults, choices, and whether they are required, etc) and includes them in `documentation.json` as well as the anvi'o help pages.

The funny thing is, anvi'o did have a means to describe all of its programs and their command line parameters through a class we implemented back in 2018, `ProgramsVignette`, which put everything anvi'o programs can do in a single resource. But we didn't have a good use for it until the arrival of LLMs. Plus, the class and its default client `anvi-script-gen-programs-vignette` wasn't even working since we moved all programs under `anvio/cli/` with entry points in `pyproject.toml` :/ With the new `DocumentationData`, it had to be reimplemented anyway.

The new version does a few things. Most importantly, it replaces the fragile design (which ran every program with `--help` in a subprocess and parsed the text it printed) with one that asks each program for the argument parser it builds without actually running the program, and reads the parameters directly from that parser rather than from the program's output (it is kinda embarrassing how we didn't do it this way the first time, but embarrassment is a part of the software development game so that's K). I also decided to combine the new implementation of it with `DocumentationData`. This way it extends Evan's design rather than keeping a parallel path. As a result, everything now comes together in a single place, so the following information for each program is accessible both programmatically and in the output of `anvi-script-gen-help-pages`, which allows anvio.org to display it (I think it would be great to link METAVARs to known artifacts to make this much more useful, but it is for another time since it is such tedious work):

<img width="978" height="1347" alt="image" src="https://github.com/user-attachments/assets/785d72cf-40fc-4e8d-b008-f6aeb9bae73d" />

I didn't change the schema version of `documentation.json` since no one is using it even though program records now carry `command_line_usage` and `parameter_groups` (i.e., the schema changed, but the version number doesn't reflect that).

Another note: programs that are not written in Python, and retired programs that only tell their users what replaces them, have no parameters listed. This may come back and bite us, but then it is something to address then.

The next broader idea is to build on `documentation.json` to give AI agents direct access to anvi'o's knowledge of itself. For instance through an MCP server (or a simpler `llms.txt` on anvio.org) that can search programs, tell an agent which parameters a program takes, and find the chains of programs that turn one artifact into another through their `requires` / `provides` relationships to build workflows, run things without guessing, etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31018814a1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.