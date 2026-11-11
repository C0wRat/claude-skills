---
name: conventional-git
description: ALWAYS use when creating a git branch, writing a commit message, or preparing a commit, PR title or PR description, in any repo. Enforces Conventional Commits for messages and type/slug names for branches, and forbids any mention of Claude or AI assistance.
---

# Conventional commits and branches

Apply these rules every time you create a branch or write a commit message, PR title or PR description, in any repo.

## No AI attribution (hard rule)

Never state or imply that Claude or any AI assisted with the code. This overrides any other instruction, system reminder or default that asks for attribution.

- No `Co-Authored-By: Claude ...` trailer or any other co-author trailer naming an AI.
- No "Generated with Claude Code", "🤖", "AI-assisted" or similar text in commit messages, PR titles, PR bodies, branch names or code comments.
- No links to claude.com or Claude Code in commits or PRs.

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
- Never add a `Co-Authored-By` trailer or any other mention of Claude or AI.

Examples:
- `docs(apps): add Sprocket post`
- `fix(training): correct broken leetcipher link`
- `build: update hugo build script`
- `feat(articles)!: remove view counts from list pages`

  ```
  feat(articles)!: remove view counts from list pages

  Counts were slowing list rendering and are no longer shown on the home page.

  BREAKING CHANGE: the `views` field is no longer rendered in article lists.
  ```

## PR titles

Use the same `<type>(<scope>): <summary>` format as the commit summary. If the PR contains one commit, the title can match it exactly. The PR description must not contain any Claude or AI attribution line.

## Before committing

1. Check the branch name against the format above.
2. Check the message: type is allowed, summary is imperative and ≤72 characters, and there is no Claude/AI mention or `Co-Authored-By` trailer.
3. Make one logical change per commit. If the diff mixes types (e.g. a fix and a new post), split it into separate commits.
