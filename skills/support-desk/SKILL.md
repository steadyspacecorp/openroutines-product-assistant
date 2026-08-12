---
name: support-desk
description: Read customer conversations from your support tool for feedback analysis. A fill-in template — adapt it to Help Scout, Intercom, Zendesk, or whatever holds your conversations, then activate the support-sync routine that uses it.
---

# Support desk

This skill is the template's worked example of extending the agent with a
tool it doesn't know: a **typed credential** in `openroutines.yml` plus a
**skill** that teaches routines the service's API. Nothing here runs
until you fill in your tool; the Help Scout example below is complete and
real — swap in your service's equivalents.

## The pattern

1. **Declare a typed credential.** Most support APIs use OAuth2 client
   credentials. Declared as `oauth2_client`, the runtime exchanges the
   stored secret at `token_url` on each run and injects only the
   short-lived bearer — routines never hold the root secret. For Help
   Scout (a "My App" under Your Profile → My Apps):

   ```yaml
   credentials:
     support_desk_secret:
       type: oauth2_client
       token_url: https://api.helpscout.net/v2/oauth2/token
       client_id: "your-app-id"
       inject_as: support_desk_token
   ```

   Then `openroutines credentials set support_desk_secret` with the app
   secret. A service that uses plain API keys instead skips the typing:
   set the key as a raw credential and it arrives verbatim as
   `$SUPPORT_DESK_SECRET`.

2. **Teach the API, read-only.** Replace the section below with the
   endpoints a feedback routine needs: list recent conversations in a
   time window, fetch one thread. Keep it to GETs — a feedback reader
   has no business writing to the support tool.

## Help Scout (example — replace with your tool)

Authentication is ambient: the bearer arrives as `$SUPPORT_DESK_TOKEN`.

- List conversations in a window, per status (never `status=all`, which
  includes spam):
  `GET https://api.helpscout.net/v2/conversations?status=<active|closed|pending>&modifiedSince=<ISO8601>`
- Fetch a thread:
  `GET https://api.helpscout.net/v2/conversations/{id}/threads`
- Strip HTML from thread bodies before reading them.

Never print, inspect, or write any credential or token to knowledge.
