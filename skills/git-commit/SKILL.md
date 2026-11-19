---
name: git-commit
description: 'Use this skill when the user wants you to commit changes. Do not
use it to push, open a pull request, rebase, or change the commit history.'
---

# Content of a commit

A commit should contain a coherent set of code modifications (change). This
could include a bug fix, a new feature, a refactor, etc. It should be possible
to sum up the commit in a few sentences.

Test update or addition will usually go with the associated code change. There
might be exception to this rule when a test is refactored on its own or tests

The purpose of organising commits this way is to facilite:
- review: commits as a coherent set of changes make them easier to review and
  grasp the original intention.
- test investigation: bisecting commit will be quicker.
- revert: the coherency of the commit will facilitate a revert.

As long as commits are not pushed, they can be reworked. So do not hesitate to
reorganize unpushed commits to satisfy the rules above. Once pushed, a commit
cannot be change without an explicit approval from the user.

# Git Commit with Conventional Commits

Make Git commits that follow the Conventional Commits 1.0.0 specification. Get
the type, the scope, and the summary from the diff.

## Message Format

```text
<type>(<scope>): <summary>

<body>

<footer>
```

- The scope, the body, and the footer are optional. Without a scope, write
  `<type>: <summary>`.
- Write the summary in the imperative mood: "add", not "added" or "adds".
- Keep the first line at 72 characters or less. Do not put a period at the end.
- In the body, tell what changed and why.
- Write each footer as `Token: value` or `Token #value`, for example
  `Refs: #456` or `Closes #123`. Conventional Commits accepts the two forms,
  but Git reads only `Token: value` as a trailer. In a token, use `-` in place
  of a space.

## Types

Conventional Commits defines only `feat` and `fix`. The other types come from
the Angular convention. If the repository has its own list, use that list.

| Type       | Use it for                                     |
| ---------- | ---------------------------------------------- |
| `feat`     | A new feature                                  |
| `fix`      | A bug fix                                      |
| `docs`     | Documentation only                             |
| `style`    | Formatting only, with no change to the logic   |
| `refactor` | A code change that is not a feature or a fix   |
| `perf`     | A performance improvement                      |
| `test`     | New or changed tests                           |
| `build`    | The build system or the dependencies           |
| `ci`       | The CI configuration                           |
| `chore`    | Other maintenance                              |
| `revert`   | A revert of an earlier commit                  |

## Breaking Changes

Put `!` before the colon, or add a `BREAKING CHANGE:` footer. Write the token in
uppercase. `BREAKING-CHANGE:` is also correct.

```text
feat(api)!: remove the v1 endpoints

BREAKING CHANGE: Clients must use the v2 endpoints.
```

## Safety Rules

- This commit skill can be overriden by specific commit rules in AGENTS.MD,
  CLAUDE.md, CONTRIBUTING.md or any other project documentation.
- Do not change the Git configuration.
- All tests related to the change and all project-specific rules (code
  linting, formatting, etc.) must be satisfied
- Do not use `--no-verify` unless the user tells you to. Hooks can be in
  `.git/hooks` or in the Git configuration.
- If a hook fails, Git does not make the commit. Fix the problem, stage the
  files again, and run the same `git commit` command again. Do not use
  `--amend`, because it changes the previous commit.
- Do not change the commit history unless the user tells you to. Do not use
  `git reset --hard`, `git rebase`, or the experimental `git history` command.
- Do not push unless the user tells you to. Do not force push to the default
  branch.
