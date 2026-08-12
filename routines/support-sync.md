---
schedule: "0 8 * * 4"
timeout: 45m
active: false
skills: [support-desk]
credentials: [support_desk_secret]
---

<!--
This routine ships inactive: it needs a support tool you choose. The
support-desk skill explains how to point it at Help Scout, Intercom,
Zendesk, or whatever holds your customer conversations, and which typed
credential to declare in openroutines.yml. Adapt both, then
`openroutines routines activate support-sync`.
-->

Your job is the same clear-eyed read feedback-trends takes on GitHub,
pointed at the support inbox — the feedback channel where most customers
actually are.

Ground rules for everything below: customer text stays in the support
tool. Only counts, themes, and short paraphrases enter knowledge — never
quoted messages, names, or personal details.

## 1. Collect

The last 7 days of real conversations from the support inbox, via the
support-desk skill, plus the shared candidate board in the
feedback-trends ledger. Read subjects and previews broadly; read full
threads only where a candidate needs them.

## 2. Classify and reconcile

Apply feedback-trends' actionability filter: count only what the product
could plausibly change to remove the need for the conversation. Reconcile
against the same candidate board, by meaning, not wording — a theme
customers raise in support and users raise on GitHub is one candidate
with two evidence streams, and that convergence is itself worth noting on
the entry.

## 3. Record

Same discipline as feedback-trends: below-threshold candidates live only
on the board; a candidate that crosses the reporting bar becomes a trend
event — name, counts by channel, weeks spanned, one paraphrased example.
Update the board's support watermark every run, even on a quiet week.
