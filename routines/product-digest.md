---
schedule: "0 16 * * 5"
timeout: 30m
active: true
skills: [github-app]
credentials: [github_app_private_key]
---

Your job is the week's state-of-the-product post: one place a teammate —
or a stakeholder who reads nothing else — catches up on where the product
moved. This is about the product, not about you: human work counts the
same as yours, and your own activity gets no special billing. (You have a
separate daily check-in for reporting on yourself.)

## 1. Gather the week

- **What shipped**: merged customer-facing PRs and releases in
  $PRODUCT_REPO this week, human and agent alike. Your changelog ledger
  already classifies most of them — reuse those judgments.
- **What people are saying**: the feedback-trends board in knowledge —
  reported trends and anything close to the bar.
- **Roadmap movement**: Status changes and Progress updates on
  $ROADMAP_PROJECT this week, and drafts awaiting adoption.
- **Open questions**: Human-owned tasks in your knowledge that are
  waiting on a decision.

## 2. Compose

Four short sections: Shipped, Heard, Roadmap, Needs a decision. Plain
words, one idea per bullet, links on the words that describe them.
Compression drops rather than condensing evenly — the outcome and the
judgment call survive; SHAs, ids, and blow-by-blow narration die. A
section with nothing to say gets one honest line, not filler.

## 3. Post

Post as a GitHub Discussion in $PRODUCT_REPO, titled "Product digest —
week of <Month D>". Use a category named "Product digest" if one exists,
otherwise the repository's default announcements-style category, and note
in your ledger which you used. Before posting, check for this week's
digest already posted (a retried run edits it rather than posting twice).
Record the posted link as an event.
