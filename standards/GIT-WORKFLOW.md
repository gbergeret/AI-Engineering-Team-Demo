# Git workflow

How this team uses git. The goal: `main` is always releasable, history stays
clean and linear, and every change is proposed and reviewed before it lands.

## Branching — trunk-based
- **`main` is always green and deployable.** No long-lived feature branches.
- Branch from `main`, merge back to `main`, and delete the branch after merge.
- Keep branches short-lived (a day or two). If a change is bigger, hide it behind
  a flag rather than letting the branch drift.
- No direct commits to `main` — every change lands through a reviewed PR.

## Branch naming
`<type>/<short-description>`, optionally with a `#<ticket>` suffix when there is a
tracker item:

```
feat/jwt-refresh-rotation
fix/payment-timeout#123
chore/upgrade-node-22
docs/add-api-runbook
```

Types: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`, `perf`, `ci`, `revert`.

## Conventional commits
```
<type>(<optional scope>): <short description>

<optional body — what and why, not how>
```

- Subject ≤ 72 characters, **imperative mood** ("add", not "added"/"adds").
- Breaking change: append `!` after the type and add a `BREAKING CHANGE:` footer.
- Reference a ticket when one exists: `feat(auth): add JWT rotation (#123)`.

Examples: `feat(auth): add JWT refresh token rotation` ·
`fix(payments): handle webhook timeout gracefully` ·
`test(orders): cover concurrent placement`.

## No AI attribution
Never put AI/assistant attribution in any git-tracked text — commit messages,
`Co-Authored-By:` trailers, PR titles or descriptions, branch names, or tags. Real
human co-authors are fine. Keep the history about the change, not the tool.

## Pull requests
- Clear title in Conventional Commits format (same rules as a commit subject).
- Description says **what** changed and **why** — the diff already shows how. A
  short "how to test" helps the reviewer.
- Lands only when QA passes (and the security gate, if the change is
  security-relevant), CI is green, and there are no merge conflicts.
- Keep the PR in sync: if you amend or drop commits, update the title and body to
  match.

## Merging and fixing
- **Rebase-merge** feature branches to keep `main` linear; rebase on the latest
  `main` before merging.
- Amend or squash work-in-progress commits so each commit on `main` is
  self-contained and passes tests — no "fix typo" commits in the final history.
- Only rewrite commits still on your own branch. Force-push your branch with
  `--force-with-lease`, never plain `--force`, and never force-push `main`.

## Pushing and hygiene
- Push with an explicit branch name (`git push -u origin <branch>` on first push),
  never a bare `git push`.
- Stage explicit paths, not broad globs that might sweep in secrets or generated
  files.
- Never commit secrets or generated files (`.env`, build output, `node_modules/`).
  If a secret ever lands, rewrite the commit to remove it **and** rotate the
  credential — git history is permanent.
- Run lint and tests locally before pushing.
