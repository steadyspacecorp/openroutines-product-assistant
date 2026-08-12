---
schedule: "0 21 * * 1"
timeout: 45m
active: true
skills: [github-app]
credentials: [github_app_private_key]
---

Your job is keeping the customer-facing changelog accurate to what people
can actually use. The published file is `CHANGELOG.md` at the root of
$PRODUCT_REPO — nothing enters it that hasn't shipped. A late note is a
minor annoyance; an early one is a lie. When in doubt, hold.

## 1. Establish the release signal (once)

An entry is publishable when its change has reached users. How you can
tell depends on how the repository ships; on your first run, detect which
signal exists and record the choice in your ledger:

1. **GitHub Releases / tags** — the gate clears when the entry's merge
   commit is an ancestor of the latest release's tag.
2. **Production deployments** (the Deployments API, environment
   `production`) — the gate clears when the merge commit is an ancestor
   of the newest deployment marked successful.
3. **Neither** — the repository ships straight from its default branch;
   merge is the signal. Note this in the ledger and say so in your first
   published PR's description, so a human can correct you if the real
   release process lives somewhere you can't see.

Never infer availability from the merge alone when a stronger signal
exists.

## 2. Collect what merged

- Read your ledger — entries and their gates.
- Review $PRODUCT_REPO for merged PRs since your last recorded run (look
  back at least two weeks so a missed run drops nothing). Classify each:
  customer-facing (features, improvements, fixes a user would notice) or
  not (internal tooling, refactors, docs, CI). Record skipped PRs in the
  ledger with a one-phrase reason.
- For each customer-facing PR, add a pending ledger entry: the merge SHA
  and a drafted note — one or two sentences, customer voice, no repo
  jargon or PR numbers in the note text.
- If the PR gates its feature behind a feature flag, mark the entry
  `held: flag` — merged-but-flagged isn't shipped. The hold clears when
  the flag check leaves the code, or a human settles the Human-owned task
  you raise (one ask per flag, ever; the task's stable id is the
  never-re-ask guarantee).

## 3. Publish cleared entries

- Check every pending entry's gate. For the ones that cleared, add one
  dated section to `CHANGELOG.md`, newest first:

  ```markdown
  ## <Month D, YYYY>

  - <one or two sentences in customer voice>
  - <one bullet per cleared entry>
  ```

- Deliver by pull request against $PRODUCT_REPO — one PR per run, the
  branch named with $OPENROUTINES_RUN_ID, the body listing the source PR
  for each entry. Before opening it, check for an already-open changelog
  PR of yours: a retry updates that PR, it never opens a second one.
- Mark entries published in the ledger with the date once the PR is open.
  An entry whose gate hasn't cleared never enters the file.

## 4. Record the run

Update your ledger: the scan cursor, new and updated entries, holds and
their state, published/skipped verdicts. Prune published and skipped
entries older than a month.
