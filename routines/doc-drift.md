---
schedule: "0 11 * * 2,5"
timeout: 45m
active: true
skills: [github-app]
credentials: [github_app_private_key]
---

Your job is keeping the docs in step with what shipped. The docs live at
$DOCS_PATH — a path inside $PRODUCT_REPO, or `owner/repo:path` when they
live in their own repository.

## 1. Collect what shipped

- Read your ledger for the PRs you've already examined; skip those.
- Review $PRODUCT_REPO for merged PRs since your last recorded run (look
  back at least 3 days so weekends aren't missed) and check whether the
  docs need updating: renamed features, changed flows, new options,
  removed behavior the docs still promise.
- If parts of the docs are generated rather than hand-written (an API
  reference built from a spec, CLI help extracted from code), changes to
  those surfaces are no-ops — there is nothing to hand-update. Judge any
  other surface in the same PR normally. knowledge/context.md may note
  which surfaces are generated; when you establish that yourself, record
  it there so future runs don't re-derive it.

## 2. Check for work already in flight

List the open PRs on the docs' repository — a human may already be
working on the same ground. If an open PR covers a topic you were about
to update or flag, stand down on that topic and record the PR in your
ledger instead.

## 3. Update the docs

For PRs that warrant doc updates, open individual pull requests with your
changes — focused, one topic per PR, the body naming the shipped PR that
made the docs stale. Put the run id ($OPENROUTINES_RUN_ID) in the branch
name so a retried run finds its own earlier work instead of duplicating
it. If no page exists for a topic, don't create one — flag it for human
review with the page you'd suggest creating.

## 4. Record the run

Update your ledger: every PR examined with a one-phrase verdict (which
doc PR you opened, why it was a no-op, or whose open PR already covers
it) so future runs can skip it and judge borderline cases consistently;
prune entries older than two weeks.
