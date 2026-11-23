---
name: build-business-website
description: Build a new website for a small business on Pancakes. Use when the person asks for a website, a landing page, or an online presence for a shop, restaurant, studio, practice or other local business. To move a site they already have, use move-my-website.
---

# Build a business website on Pancakes

The Pancakes connector creates a real site that the person owns. Work in this
order and keep the person in charge of every step that changes what the public
sees.

## 1. Learn about the business

Ask only what you cannot infer, a few questions at a time:

- The business name, what it sells or does, and for whom
- Where it is, its hours, and how customers reach it (phone, email, booking)
- The pages they want. Most small businesses need Home, About, Services or
  Menu, and Contact. Do not add pages they did not ask for
- Photos they own, as links, and whether they have a logo

Use the person's own words for their business. Do not invent prices, awards,
reviews, staff names, years in business or claims they did not give you. Leave
a clear placeholder instead and tell them what is missing.

## 2. Choose a theme together

Call `list_themes` with a few words about the business. It works before
sign-in. Suggest two or three themes whose `suits` match, with their
`previewUrl`, and let the person pick a theme and palette.

## 3. Create the site

Call `create_site` with `name`, a `brief` of two or three sentences, and the
chosen `themeId` and `colorwayId`. Building and previewing need no plan. The
new site is not public. Keep its `id` and pass it as `site` to every later
tool.

- If the person is signed in to Pancakes, the site is made in their
  workspace. Give them its `editUrl` so they can look at it in Pancakes at
  any time.
- If nobody is signed in, the site is a draft that no account owns yet. You
  can still read it, write its pages and show previews. Give the person its
  `claimUrl` and tell them the draft is deleted after a week unless they
  open that link and sign in or create a free account. Publishing, adding
  photos and scheduling ask them to sign in; keep using the same `site`
  value afterwards.
- If the person says they already have a Pancakes account, call `list_sites`
  first, which asks them to sign in, so the site is made in their workspace.

## 4. Write the pages

1. Call `get_page` with `page: "home"` to read the starter blocks and their
   field paths.
2. Replace the starter text with `propose_changes`. Group related edits into
   one change, for example the hero heading, its text and its button.
3. Add pages with the `add_page` verb and blocks with `add_section`. Give a
   new block a `tempId` and fill it in the same change.
4. For photos, call `import_image` with links the person owns, then use the
   returned URL in `set_media` with alt text that says what the photo shows.

Each proposal returns before and after pictures, and in Claude and ChatGPT a
preview card with Apply and Discard buttons. Show the person the preview and
call `apply_changes` only when they approve. While the site has never been
published, every change can be approved this way. If the owner turned on
"Changes from connected apps wait for my approval", or once the site has been
online, changes to pages, blocks, links and images wait in the Pancakes
dashboard instead; give the person the review link the tool returns.

## 5. Check and publish

1. Call `get_readiness`. Fix every error (broken links, buttons with no link,
   forms with no fields) with the person, and mention warnings such as
   leftover starter text.
2. Ask the person whether to publish. Call `publish_site` only after they say
   yes. Then share the public URL it returns.
   - If it returns `online: false` with a `launchUrl`, the workspace's plan
     does not include publishing yet. Give the person that link: it opens the
     site in Pancakes, where they can publish it. Do not describe plans or
     prices yourself.
3. Tell them they can connect their own domain later (see the
   `connect-a-domain` skill) and edit anything in the Pancakes editor.
