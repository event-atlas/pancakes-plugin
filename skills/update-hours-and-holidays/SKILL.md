---
name: update-hours-and-holidays
description: Change a business's opening hours on its Pancakes website, permanently or for a holiday, closure or special event. Use when the person mentions hours, being closed, a holiday schedule, a snow day, or opening late or early.
---

# Update hours and holiday hours

1. Call `list_sites` if you do not know the site, then `get_site` and
   `get_page` to find where hours appear. Hours usually live in a Contact and
   hours block and are often repeated in a notice or footer; change every place
   they appear so the site never shows two answers.
2. Ask whether the change is permanent or for a date range. Read times in the
   site's timezone, which `get_site` reports.
3. Permanent change: `propose_changes`, show the preview, then
   `apply_changes` when the person approves.
4. Temporary change: `propose_changes`, then `schedule_changes` with `applyAt`
   at the start of the first changed day and `revertAt` when regular hours
   resume. Pancakes puts the regular hours back by itself at `revertAt`. Tell
   the person both times in their local time.
5. For a closure announced on the day, a short notice near the top of the home
   page helps visitors. Propose it in the same change as the hours so both go
   live and come down together.

Use `list_changesets` to find hours changes that are already scheduled before
adding another, and `reschedule_change` or `cancel_scheduled_change` to move
or drop one.
