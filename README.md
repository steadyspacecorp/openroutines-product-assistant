An assistant for product teams, built on [OpenRoutines](https://openroutines.dev). It
runs the loop your team knows it should run but never has time for:
feedback in, roadmap current, docs true, shipped work told back to
customers — and a daily check-in where your team talks.

Everything it does is visible where you already work: labels and comments
on your issues, fields on your roadmap Project, pull requests against
your docs and changelog, a weekly digest in Discussions, and a standup
update in Slack.

## The routines

| Routine | What it does |
|---|---|
| feedback-triage | Labels new issues and discussions, links duplicates, asks for missing repro or context. Never closes, never promises. |
| feedback-trends | Clusters the week's feedback into themes, tracks evidence on a candidate board, reports only trends with sustained evidence. |
| roadmap-groomer | Keeps the roadmap Project true to the code: owns the `Status` and `Progress` fields, drafts items from reported trends, never reprioritizes. |
| doc-drift | Compares merged PRs against the docs and opens focused fix PRs; flags what needs a human. |
| changelog | Turns shipped, customer-facing PRs into plain-language `CHANGELOG.md` entries, by PR, gated on the change actually being released. |
| product-digest | Posts the week's state of the product — shipped, heard, roadmap, needs-a-decision — as a GitHub Discussion. |
| slack-report | The agent's own daily check-in, posted to your Slack channel: what it did, what it will do, where it needs a human. |
| support-sync | The trends lens pointed at your support tool. Ships inactive until you adapt the `support-desk` skill to Help Scout, Intercom, Zendesk, etc. |

Each routine states its own boundary between what it fixes and what it
flags. The agent makes mechanical changes itself and files a task for
anything that needs judgment — read any file in `routines/` to see
exactly what it may touch.

## Take it for a spin

Every working routine has a rehearsal scenario in `rehearsals/` — one
consistent fictional product (Relay, a shared team inbox) with a week of
feedback, merges, a release, and a roadmap. A fixtured rehearsal strips
all credentials and never writes anything, so this works before any
setup beyond the CLI and Docker:

```bash
openroutines routines run feedback-trends --rehearse
openroutines routines run changelog --rehearse
openroutines routines run roadmap-groomer --rehearse
```

Each prints exactly what it would have done — the board it would keep,
the PR it would open, the note it would hold back and why. Edit a
prompt, rehearse again, watch the judgment change. That's the
[write–rehearse–run loop](https://openroutines.dev/docs/local-development/)
you'll use for routines of your own.

## Setup

You need the [OpenRoutines CLI](https://openroutines.dev/docs/getting-started/)
and about ten minutes.

1. **Use this template** to create your agent's repository, and clone it.
2. `openroutines configure` — fills in the owner, timezone, and model,
   and generates the `master.key` that encrypts credentials (back it up;
   it stays out of git).
3. Set the variables in `openroutines.yml`: your product repository, your
   roadmap's GitHub Project URL, where the docs live — and the same repo
   in `routines/feedback-triage.md`'s trigger URL.
4. GitHub, as an App — so the agent's PRs, comments, and commits are its
   own, not yours, and each run gets a short-lived installation token
   instead of a long-lived personal one. Create a GitHub App
   ([Settings → Developer settings → GitHub Apps](https://github.com/settings/apps/new)):
   name it after your agent, deactivate the webhook, and grant repository
   permissions Contents, Issues, Pull requests, Discussions (read and
   write) plus organization permission Projects (read and write). Install
   it on your product repo, then put the App ID in `openroutines.yml` and
   store the key:
   `openroutines credentials set github_app_private_key < your-app.private-key.pem`
5. Slack, so the agent can check in like a teammate: create the
   two-scope Slack app described in
   `.openroutines/plugins/slack-report/PLUGIN.md`, then
   `openroutines credentials set slack_bot_token`, invite the bot to your
   channel, and put the channel ID in the `slack_channel` variable.
   Verify the wiring:
   `OPENROUTINES_LOG_LEVEL=warn openroutines routines run slack-verify --no-knowledge`
6. `openroutines check`, commit, and
   [deploy](https://openroutines.dev/docs/deploying/).

This is your teammate now — rename it in `openroutines.yml`, retune the
schedules, and edit the routine prompts like any other file in your repo.
Prefer the check-in somewhere else? Swap the destination:
`openroutines plugin add steadyspacecorp/openroutines-plugins --path discord-report`
(or `--path steady`).

## Working on this agent

```bash
openroutines status                # what the agent has and still needs
openroutines sync                  # pull the latest knowledge; read the files under knowledge/
openroutines routines new <name>   # add a routine
openroutines routines run <name>   # real run; knowledge writes discarded (--write-knowledge settles)
openroutines check                 # validate everything; run it in CI
```

Deploying, updating, and everything else:
[OpenRoutines documentation](https://openroutines.dev).
