# 001 - PR digest

**Cadence:** Daily (scheduled). Set this up as a recurring routine in Claude Code
so it runs each morning.

A short morning digest of the open pull requests, built from GitHub. Read-only. The
Architect runs it (it holds the GitHub read tools).

## Steps
1. List the open pull requests (`list_pull_requests` for this repo).
2. For each, read its state (`pull_request_read`): how old it is, who it is waiting
   on, whether it is approved or still in review.
3. Summarise: how many are open, which are ready to merge, which are stale or
   blocked, and anything waiting on you.
4. Keep it tight — a few lines, concise and to the point.

## Output
Present the digest in chat. Change nothing on GitHub, this is read-only (pushes,
PRs, and merges are denied).

## Done when
The digest covers the open PRs and flags what is ready, stale, or waiting on you —
or says there are no open PRs.
