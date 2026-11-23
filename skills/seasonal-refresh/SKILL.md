---
name: seasonal-refresh
description: Plan and schedule seasonal updates on a Pancakes website, such as a holiday menu, a summer offer, a sale banner or event dates, that go live on one date and come down on another. Use when the person mentions a season, a promotion with dates, an upcoming event or a limited-time menu.
---

# Seasonal refresh

1. Ask what changes, when it starts, and when it ends. Get the exact offer,
   prices and dates from the person; never invent them.
2. Read the affected pages with `get_page`. Prefer changing existing blocks
   over adding new ones, so the page returns to its usual shape when the
   season ends.
3. Call `propose_changes` with every edit for the season in one change, and
   show the preview.
4. Call `schedule_changes` with `applyAt` and `revertAt`. At `revertAt`,
   Pancakes restores the content that was there before. Use `preview_site`
   with `at` to show the person how the site will look on a date inside the
   season.
5. List everything the person has scheduled with `list_changesets` when they
   ask what is coming up, and remind them that the site calendar in the
   Pancakes dashboard shows the same plan.

Scheduling needs a plan that includes scheduled changes. If a tool says the
plan does not include it, apply the change now instead if the person agrees,
and share the plans page link the tool returns.
