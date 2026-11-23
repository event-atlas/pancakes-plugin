---
name: weekly-site-checkup
description: Review a Pancakes website for stale or broken content and suggest fixes. Use when the person asks to check, audit, review or tidy their site, or asks whether anything on it is out of date.
---

# Weekly site checkup

1. Call `list_sites`, then for the chosen site call `get_readiness` for
   broken links, empty buttons, missing forms and starter text.
2. Read each visible page with `get_page` and look for content that has gone
   stale: past dates and events, expired offers, seasons that have ended,
   "new" items that are no longer new, and hours that disagree between pages.
3. Call `list_changesets` to see what is already scheduled, so you do not
   suggest something the person has planned.
4. Report what you found in a short list, most important first, with the page
   each item is on. Ask which ones to fix.
5. Fix the chosen items with `propose_changes`, show each preview, and apply
   or schedule only what the person approves.

Do not rewrite content that is correct just to change its style.
