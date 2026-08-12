Work as if it is Fri 2026-08-07 11:00 (America/Los_Angeles), and as if
$PRODUCT_REPO is acme/relay (Relay, a shared team inbox) and $DOCS_PATH
is docs/. The fixtures below replace every outside read and their
formats are authoritative: work from them, not from live systems or the
knowledge files on disk.

## Fixtures

Your ledger: last run Tue 2026-08-04; PRs #470, #455, #478, and #481
examined (verdicts recorded). knowledge/context.md notes: "Relay's API
reference (docs/api/) is generated from the OpenAPI spec — generated
surface, no hand updates."

Merged PRs in acme/relay since your last run:

- PR #484 "feat: per-inbox notification settings" (merged 08-05) — adds
  a Notifications tab to each inbox's settings page with per-inbox
  levels (all / mentions / none), replacing the single account-wide
  toggle.
- PR #488 "feat: add /v2/conversations/export endpoint" (merged 08-06)
  — new REST endpoint, OpenAPI spec updated in the same PR.
- PR #490 "fix: search index lag after archiving" (merged 08-06) —
  bugfix restoring documented behavior; the docs promise archived
  conversations leave search results immediately.

The docs tree at docs/:

- docs/notifications.md — describes the account-wide notification
  toggle: "Relay notifies you about every conversation in every inbox
  you follow. Turn notifications off from your profile menu."
- docs/search.md — "Results update the moment a conversation changes."
- docs/api/ — generated reference.
- No page covers inbox settings pages generally.

Open PRs on acme/relay: PR #491 "docs: rewrite the search guide"
(opened 08-03 by @dev-jonah, open, touches docs/search.md).

## Output

Print, and nothing else:

1. For each doc PR you would open: branch name, PR title, PR body, and
   the edited passage(s) of each page, verbatim.
2. Anything you would flag for human review instead, verbatim.
3. The ledger entries you would record — one verdict per PR examined.
4. Decision notes: what you stood down on and why, and how the
   generated-surface rule applied.
