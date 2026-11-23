---
name: update-my-site
description: Make an everyday change to a Pancakes website, such as new text, a price, a photo, a button or a page, undo a change, or move or cancel a scheduled change. Use when the person asks to change, fix, add, remove, replace or undo something on their site. For opening hours use update-hours-and-holidays; for dated promotions use seasonal-refresh.
---

# Update a Pancakes site

Every change is proposed first, previewed, and applied only when the person
says yes. Never apply, undo, cancel or publish on your own judgment.

## 1. Find the content

1. Call `list_sites` if you do not know the site, then `get_site` for its
   pages and settings (site name, header, footer, search descriptions).
2. Call `get_page` for each page the change touches. Use the block ids and
   field paths it returns; do not guess them.
3. If the same detail appears in several places (a phone number, a price, an
   address), change every place in one proposal and tell the person where.

## 2. Propose and preview

1. Call `propose_changes` with every edit for the request in one change.
   Keep the person's wording. Do not invent prices, claims, reviews or names.
2. Show the before and after preview the tool returns. If the person wants
   something different, call `revise_changeset` on the same change rather than
   starting a new one.
3. Call `apply_changes` only after the person approves.

Some changes wait for approval in the Pancakes dashboard instead: on a site
that has been published, changes to pages, links, buttons, the header and
footer, and removals; and every change when the owner turned on "Changes from
connected apps wait for my approval". Give the person the review link the
tool returns and say the change is waiting there.

## Photos

- A photo the person shared in the chat or has on their computer:
  `upload_image` with the file's bytes.
- A photo at a public link the person owns: `import_image`.
- A photo already in the site's library: `list_media`.

Then use the returned URL in a `set_media` edit, with alt text that says
what the photo shows. Only use images the person owns or has the right to
use.

## Undo a change

Call `list_changesets` to find it, confirm with the person which change they
mean, then `undo_change` with its `changesetId`. If Pancakes refuses because
later edits changed the same content, tell the person which edits, and offer
to propose the old content as a new change instead.

## Scheduled and held changes

- What is coming up: `list_changesets`, then `get_changeset` for detail.
- Move one: `reschedule_change` with the new `applyAt` (and `revertAt`).
  Tell the person both times in the site's timezone from `get_site`.
- Stop one: `cancel_scheduled_change`. Cancelling a scheduled reversion keeps
  the change it would have reverted; say so before cancelling.
- A change held because the site changed after it was approved:
  `approve_held_change`. When it returns a fresh preview instead of
  approving, show that preview and call it again only after the person agrees.

To show how the site will look on a date, call `preview_site` with `at`. For
a link the person can open in the dashboard, call `get_preview_link`.
