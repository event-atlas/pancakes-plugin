---
name: move-my-website
description: Move a business website the person already has (Squarespace, Wix, WordPress, Shopify, Showit, Framer, Lovable or hand-built) to Pancakes. Use when the person asks to move, switch, migrate, transfer or import their current site.
---

# Move a website to Pancakes

Pancakes copies the old site's pages, text, images, links and forms into a
new, private Pancakes site. The import runs on Pancakes, not in this
conversation, and it does not change or take down the old site.

## 1. Confirm before importing

Ask, in one message:

- The website's address
- That they own the website or have the owner's permission to copy it. Do not
  import a site until they say yes
- Whether to keep the site's look ("match": Pancakes writes a theme with its
  colors, fonts and layout) or rebuild it on a Pancakes theme ("new"). If they
  are unsure, call `list_themes` and show two or three that suit the business
- Anything to leave out or emphasize, such as an old page or a menu that
  changed. This is optional

## 2. Start the import

Call `import_site` with `url`, `name` (the business name), `ownerConfirmed:
true`, `look` and, if they gave any, `notes`. The app signs the person in to
Pancakes the first time; someone new can create a free account in that
window. Importing needs a verified email address, so if the tool says the
email is unverified, ask them to open the link Pancakes emailed them.

A workspace's first import is free. If `import_site` says the workspace has
used it, give the person the plans link from the message. Do not describe
plans or prices yourself.

Keep the import `id` and tell the person the import is running and where to
watch it (`transferUrl`).

## 3. Follow it

Call `get_import` with the id every minute or two. Tell the person when it
reaches a new stage, not on every call. It usually takes several minutes.

- `ready`: the site is built. Keep its `siteId` and give the person the
  `editUrl`.
- `action_required`: a step needs the person. Give them the `error` and the
  `transferUrl`, where they can continue it.
- `failed`: give them the `error` and the `transferUrl`, where they can retry.

## 4. Review it together

1. Call `get_page` with `site` set to the new `siteId` and `page: "home"`, and
   compare it with the old home page. Point out anything missing or wrong:
   hours, prices, phone numbers, staff, menus.
2. Fix what the person wants with `propose_changes`. Show each preview and
   call `apply_changes` only when they approve.
3. Call `get_readiness` and fix every error with them.
4. Ask whether to publish. Call `publish_site` only after they say yes. If it
   returns a `launchUrl`, give them that link to choose a plan and publish.

## 5. After publishing

The old site keeps running until the person cancels it. Tell them to point
their domain at Pancakes (see the `connect-a-domain` skill) before they
cancel their old plan, so the address never goes dark.
