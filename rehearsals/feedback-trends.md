Work as if it is Thu 2026-08-06 09:00 (America/Los_Angeles), and as if
$PRODUCT_REPO is acme/relay (Relay, a shared team inbox) and
$ROADMAP_PROJECT is https://github.com/orgs/acme/projects/4. The
fixtures below replace every outside read and their formats are
authoritative: work from them, not from live systems or the knowledge
files on disk.

## Fixtures

Your ledger's candidate board (window covered through 2026-07-29):

```markdown
## Candidates

- **Notification noise** — people want quieter, finer-grained
  notifications. Count 4 (weeks of 07-20, 07-27). Example:
  [#463](https://github.com/acme/relay/issues/463) "notifications for
  every reply in threads I'm not part of". Roadmap: no covering item.
- **Bulk actions** — archive/assign many conversations at once. Count 2
  (week of 07-27). Example: [#471](https://github.com/acme/relay/issues/471).
  Roadmap: no covering item.

## Reported

- **Conversation export** — reported 2026-07-30 (count 5 over 3 weeks).
  Roadmap: no covering item.
```

New issues, discussions, and issue comments in acme/relay, 07-30 →
08-06:

- Issue #482 (08-03): "Let me mute a single conversation" — long thread,
  two more users +1'd.
- Issue #485 (08-04): "Per-inbox notification settings" — loud for
  support, quiet for sales.
- Issue #486 (08-04): "Search returns stale results" — a bug report,
  awaiting repro details.
- Issue #489 (08-05): "Export conversations to CSV" — for a quarterly
  compliance review.
- Discussion "Snooze is great" (08-05): praise for the snooze beta, one
  aside wishing snooze times were configurable.

Also in the repo: PR #484 "feat: per-inbox notification settings"
merged 2026-08-05, no release contains it yet.

The roadmap Project's items: "Faster search" (Status: Now), "Snooze
conversations" (Status: Now), "Mobile app" (Status: Later), "Email
templates" (no Status), "Onboarding revamp" (Status: Done). Nothing
covers notifications or export.

## Output

Print, and nothing else:

1. The full updated candidate board, verbatim.
2. Every event line you would record, verbatim — and for any candidate
   that did NOT become an event, why.
3. Decision notes: what you merged by meaning, what you held aside as
   possibly by-design or not actionable, and how the merged-but-unreleased
   PR #484 figured into your judgment.
