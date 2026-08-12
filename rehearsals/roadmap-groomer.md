Work as if it is Tue 2026-08-04 17:00 (America/Los_Angeles), and as if
$PRODUCT_REPO is acme/relay (Relay, a shared team inbox) and
$ROADMAP_PROJECT is https://github.com/orgs/acme/projects/4. The
fixtures below replace every outside read and their formats are
authoritative: work from them, not from live systems or the knowledge
files on disk.

## Fixtures

Your ledger: last run Tue 2026-07-28; PRs through #469 judged. The
Done-set holds: "Legacy importer". No drafts awaiting adoption.

The Project (both expected fields exist; Status options are Now, Next,
Later, Done):

- **Faster search** — Status: Now. Progress: "Query rewrite landed
  (v1.41)." Linked: issue #438 (open), PR #470.
- **Snooze conversations** — Status: Now. Progress: empty. Linked:
  issue #440 (closed), PR #455.
- **Mobile app** — Status: Later. Progress: empty. No linked work.
- **Email templates** — no Status. Progress: empty. No linked work.
- **Onboarding revamp** — Status: Done (moved 2026-08-02 by @mara-cho).
  Linked: issue #452 (closed), issue #472 (open: "empty-state copy for
  the new flow").
- **Legacy importer** — Status: Done (since June).

Merged PRs in acme/relay since your last run:

- PR #470 "perf: incremental search indexing" (merged 07-28) — linked to
  issue #438; the release notes ledger shows it shipped in v1.42.0
  (07-31).
- PR #478 "fix: attachment previews in Safari" (merged 08-03) — plain
  bugfix, links to no item.
- PR #481 "chore: parallelize CI" (merged 08-03).

Your knowledge holds one reported feedback trend not yet on the board:
**Conversation export** — reported 2026-07-30, 5 reports over 3 weeks,
example [#465](https://github.com/acme/relay/issues/465), roadmap: no
covering item.

## Output

Print, and nothing else:

1. Every Project write you would make, one line each: the item, the
   field, and the exact new value (Progress text verbatim).
2. Any draft item you would add: its full title and body, verbatim.
3. Any Human-owned task you would raise, verbatim.
4. Every event line, verbatim.
5. The ledger updates, verbatim — including your PR→item judgments and
   the new Done-set.
6. Decision notes: any Status move you considered and held back from,
   and why.
