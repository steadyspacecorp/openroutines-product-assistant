Work as if it is Mon 2026-08-03 21:00 (America/Los_Angeles), and as if
$PRODUCT_REPO is acme/relay — Relay, a shared team inbox. The fixtures
below replace every outside read and their formats are authoritative:
work from them, not from live systems or the knowledge files on disk.

## Fixtures

Your ledger:

```markdown
Release signal: GitHub Releases (established 2026-07-13).
Scan cursor: Mon 2026-07-27 21:00.

## Pending

- relay#455 "Snooze conversations" (merged 07-20, sha a1b2c3d) — note
  drafted: "Snooze a conversation and it comes back to the top of your
  inbox when you're ready for it." Held: flag `snooze_v2`. GA ask open
  as task-20260720-2.

## Published / skipped

- relay#461 — published 07-27.
- relay#466 "chore: dependency bumps" — skipped, internal.
```

Merged PRs in acme/relay since your cursor:

- PR #470 "perf: incremental search indexing" (merged 07-28, sha
  9f8e7d6) — search results now update within seconds of a change
  instead of on a five-minute rebuild.
- PR #478 "fix: attachment previews in Safari" (merged 08-03, sha
  4c5d6e7) — PDF previews were spinning forever for Safari users.
- PR #481 "chore: parallelize CI" (merged 08-03).

Releases: latest is v1.42.0, tagged 2026-07-31. Its tag contains the
merge commits of #455 and #470. It does not contain #478 or #481.

The code at v1.42.0 still checks the `snooze_v2` flag. Task-20260720-2
is still open, unanswered.

CHANGELOG.md currently ends its newest section at "## July 27, 2026".

## Output

Print, and nothing else:

1. The updated ledger, verbatim — every entry with its gate state.
2. The new CHANGELOG.md section you would publish, verbatim — and the
   PR delivering it: branch name, title, body.
3. Decision notes: per entry, why it published, held, or skipped —
   including exactly why #455 is in v1.42.0 but not in the changelog.
