---
name: conventional-git
description: Use when creating a git branch, writing a commit message, or preparing a commit or PR title in this repo. Enforces Conventional Commits for messages and Conventional-style type/slug names for branches.
---

# Conventional commits and branches

Apply these rules whenever you create a branch or write a commit message in this repo.

## Branch names

Format: `<type>/<short-kebab-description>`

- `<type>` is one of the types listed below.
- The description is 2–5 lowercase words separated by hyphens. No spaces, no uppercase, no underscores, no trailing slash.
- Use the same type as the main change you are making.

Examples:
- `feat/sprocket-post`
- `fix/broken-leetcipher-link`
- `docs/byte-serpent-date`
- `chore/update-hugo-build`

If the current branch is not in this format and you are about to start new work, create a new branch from `main` using this format rather than committing to the existing one. Never commit directly to `main`.

## Commit messages

Format:

```
<type>(<optional scope>): <imperative summary>

<optional body explaining why, wrapped at ~72 columns>

<optional footer, e.g. BREAKING CHANGE: ... or Refs: #123>
Co-Authored-By: Claude Haiku 5.5 <noreply@anthropic.com>
```

Rules:
- **Type** is required and lowercase. Allowed types:
  - `feat` — new user-visible feature or content
  - `fix` — bug fix
  - `docs` — content or documentation (blog/training posts, README)
  - `style` — formatting only, no behavior change
  - `refactor` — code change that neither fixes a bug nor adds a feature
  - `perf` — performance improvement
  - `test` — adding or fixing tests
  - `build` — build system or dependencies (Hugo, npm, go modules)
  - `ci` — CI/CD and deploy workflow configuration
  - `chore` — maintenance that fits nowhere else
  - `revert` — reverts an earlier commit
- **Scope** is optional, lowercase, and names the area touched (e.g. `apps`, `training`, `theme`, `deploy`). Omit it if no single area fits.
- **Summary**: imperative mood ("add", "fix", "update"), lowercase first word, no trailing period, 72 characters or fewer.
- **Body** (optional): explain *why*, not what. Separate from the summary with a blank line.
- **Breaking changes**: add `!` after the type/scope (`feat(api)!: ...`) and a `BREAKING CHANGE: <description>` footer.
- Put the `Co-Authored-By` trailer last, as shown above.

Examples:
- `docs(apps): add Sprocket post`
- `fix(training): correct broken leetcipher link`
- `build: update hugo build script`
- `feat(articles)!: remove view counts from list pages`

  ```
  feat(articles)!: remove view counts from list pages

  Counts were slowing list rendering and are no longer shown on the home page.

  BREAKING CHANGE: the `views` field is no longer rendered in article lists.
  Co-Authored-By: Claude Haiku 5.5 <noreply@anthropic.com>
  ```

## PR titles

Use the same `<type>(<scope>): <summary>` format as the commit summary. If the PR contains one commit, the title can match it exactly.

## Before committing

1. Check the branch name against the format above.
2. Check the message: type is allowed, summary is imperative and ≤72 characters, trailer present.
3. Make one logical change per commit. If the diff mixes types (e.g. a fix and a new post), split it into separate commits.
