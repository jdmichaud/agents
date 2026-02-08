---
name: Git commit
description: Set of rules to follow when committing changes in a git based
project.
---

# Git commit

This skills will help you produce well organized and helpfull git commit.

# When to use the skill

Use this skill whenever committing changes to any git based project.

# Content of a commit

A commit should contain a coherent set of code modifications (change). It should
be possible to sum up the commit in a few sentences. Commit message should not
reference immediate commit changes otherwise, it means that those commit could
be merged into one. Conversely, you should not have to resume a commit with
multiple paragraph of too long a text. It probably means that the commit can be
split into smaller one.

# When to commit

Committing to a project should be done only when the test associated with the
changes are passing and when all the project specific rules for a commit are
satisfied (code linting, formatting, etc). Prefer let the user review the
changes before committing. If no comments were made before moving on to the next
request, assume that the user is OK with the change to be committed.

# Commit message.

Follow the common good practices for commit messages.

Make sure to document design trade-offs or remaining tasks associated with the
change in the commit message if applicable.

# Rules to follow

- Never push. Let the use handle pushing or retrieving changes from a git
  remote.

- Never rewrite history on already pushed changes unless explicitely asked.
  Amending local commit is acceptable.

- If the project contains a README.md, AGENTS.md or a DESIGN.md, make sure that
  the files are still up to date following the change you are about to commit.
  If not, update them and include them in the commit.