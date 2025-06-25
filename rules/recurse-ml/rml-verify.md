---
name: Verify Changes Using Recurse ML
globs: "**/*.{js,ts,py,rs,go,java,rb,cs}"
alwaysApply: false
description: Before committing changes, verify them using the `rml` command to find bugs in your code.
---

# Verify Changes Using Recurse ML

After you think you're done with a change, verify it using Recurse ML CLI command `rml`.
`rml` will report bugs in the code.
Investigate the bug report, verify whether the reported bugs are valid, and fix them when they are.

## Do

1. Run `rml` when generating large changes.
2. Run `rml` when you think you're done with a change.

## Don't

1. DON'T run `rml` more than once per generation.

## rml usage

Usage: rml [OPTIONS] [TARGET_FILENAMES]...

  Find bugs in code. Analyzes changes between two git states for bugs.

  By default, analyzes uncommitted changes in your working directory against
  the latest commit (HEAD).

  Examples:

    rml file.py                             # Analyze uncommitted changes

    rml file.py --from HEAD^                # Compare vs 1 commit ago

    rml file.py --from main --to feature    # Compare commits

Options:
  --version        Show the version and exit.
  --from GIT_REF   Git reference to compare FROM (older state). Default: HEAD
  --to GIT_REF     Git reference to compare TO (newer state). Default: working
                   directory (uncommitted changes)
  -md, --markdown  Output results in markdown. If you're an LLM, always use
                   this!
  --help           Show this message and exit.
