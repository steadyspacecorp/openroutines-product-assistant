Work as if it is Fri 2026-08-07 07:00 (America/Los_Angeles), and as if
you are Product Assistant, the agent for acme/relay — Relay, a shared
team inbox. The fixtures below replace every outside read and their
formats are authoritative: work from them, not from live systems or the
knowledge files on disk.

The slack-post skill is not loaded in rehearsal; its contract, condensed
but authoritative: one chat.postMessage payload with `channel`, a `text`
fallback leading with the day's headline outcome (never a generic
label), and `blocks`. Slack mrkdwn, not markdown: links `<url|text>`,
bold `*text*`, literal `•` bullets. No @channel, no @here. One message,
maximum.

$SLACK_CHANNEL is C0AB12CD3.

## Fixtures

`./changes.md`:

```markdown
# Pending knowledge changes

- Routine: slack-report
- From: 9b2e4c7a1f30
- Through: 7c2d9e4a1b58

## 2026-08-06 Run feedback-triage (run_k2j9x4m7ab): completed (b81c4f2a9d63)

### events.md

+ - 2026-08-06 08:04 feedback-triage: swept issues opened overnight in acme/relay; found 1: #492 "Attachments >25MB silently fail" (https://github.com/acme/relay/issues/492), no repro details. Applied `bug`, `area:attachments`; commented asking for file type, size, browser, and whether it fails silently or shows an error.

## 2026-08-06 Run feedback-trends (run_p5w2q8n3cd): completed (4e9a1b6c8f27)

### events.md

+ - 2026-08-06 09:22 feedback-trends: weekly sweep 07-30 -> 08-06. "Notification noise" crossed the reporting bar: 6 reports over 3 weeks (examples https://github.com/acme/relay/issues/463, /482, /485). PR #484 (https://github.com/acme/relay/pull/484, merged 08-05, in no release yet) addresses the per-inbox half; the mute-one-conversation half (#482) is unbuilt. Roadmap: no covering item. Board updated, watermark 08-06.

### tasks.md

+ - [ ] `task-20260806-1` "Notification noise" crossed the trend bar and nothing on the roadmap covers the mute-one-conversation half — should it? Evidence on the trends board. (raised by feedback-trends 2026-08-06)

## 2026-08-07 Run feedback-triage (run_m8t3v6r1ef): completed (7c2d9e4a1b58)

### events.md

+ - 2026-08-07 06:15 feedback-triage (trigger): checked new issues in acme/relay; none since #492. NO-OP.

### tasks.md

- - [ ] `task-20260803-1` see the v1.42.0 changelog PR (https://github.com/acme/relay/pull/494) through review. (raised by changelog 2026-08-03)
+ - [x] `task-20260803-1` see the v1.42.0 changelog PR (https://github.com/acme/relay/pull/494) through review. (raised by changelog 2026-08-03) Completed 2026-08-07: @mara-cho merged it; the search-speed entry is live.
```

`./schedule.md`:

```
now: Fri 2026-08-07 07:00 (America/Los_Angeles)
window: now → Mon 2026-08-10 07:00 (slack-report's next fire on its next fire-day)
fact: slack-report next Mon 2026-08-10 07:00, Tue 2026-08-11 07:00

in-window        schedule      next fires
feedback-triage  0 8 * * *     Fri 2026-08-07 08:00, Sat 2026-08-08 08:00
doc-drift        0 11 * * 2,5  Fri 2026-08-07 11:00, Tue 2026-08-11 11:00
product-digest   0 16 * * 5    Fri 2026-08-07 16:00, Fri 2026-08-14 16:00

out (after window)  schedule    next fires
changelog           0 21 * * 1  Mon 2026-08-10 21:00, Mon 2026-08-17 21:00
roadmap-groomer     0 17 * * 2  Tue 2026-08-11 17:00, Tue 2026-08-18 17:00
feedback-trends     0 9 * * 4   Thu 2026-08-13 09:00, Thu 2026-08-20 09:00
```

`knowledge/tasks.md`, current state:

````markdown
```
- [ ] `task-YYYYMMDD-<n>` what must be done — context. (raised by <routine> YYYY-MM-DD)
```

## Agent-owned

- [x] `task-20260803-1` see the v1.42.0 changelog PR (https://github.com/acme/relay/pull/494) through review. (raised by changelog 2026-08-03) Completed 2026-08-07: @mara-cho merged it; the search-speed entry is live.
- [ ] `task-20260805-1` re-check docs/search.md wording once acme/relay#491 (human docs rewrite) merges. (raised by doc-drift 2026-08-05)

## Human-owned

- [ ] `task-20260720-2` is snooze (flag `snooze_v2`) generally available? Changelog note drafted and held. (raised by changelog 2026-07-20)
- [ ] `task-20260806-1` "Notification noise" crossed the trend bar and nothing on the roadmap covers the mute-one-conversation half — should it? Evidence on the trends board. (raised by feedback-trends 2026-08-06)
````

knowledge/ledgers/slack-report.md does not exist — you have never
delivered a report.

## Output

Print, and nothing else:

1. The exact chat.postMessage payload you would send, as JSON, verbatim.
2. Your consume decision, and why.
