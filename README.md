# Pancakes

Build and run a small-business website from a conversation with Claude,
ChatGPT, Codex or another agent. Pancakes hosts the site; this plugin connects
your agent to it and teaches the agent how Pancakes works.

## What you can ask for

- "Make a website for my bakery in Providence." The agent asks a few
  questions, picks a theme with you, writes the pages, shows you a preview and
  publishes when you say so.
- "Post our holiday hours for Thanksgiving week and put the regular hours back
  after." The change is scheduled, previewed, and reverts on its own.
- "Check my site before I publish it." The agent runs the pre-publish checks
  and fixes broken links, missing forms and leftover starter text with you.

Every edit is proposed first, with before and after pictures. Nothing on your
site changes until you approve it. Once a site has been published, changes to
pages, blocks, links and images wait for approval in the Pancakes dashboard,
and you can make every change wait there.

## Setup

In Claude Code, run these two commands in a terminal:

```sh
claude plugin marketplace add event-atlas/pancakes-plugin
claude plugin install pancakes@pancakes
```

Or install the copy that Pancakes serves, without GitHub:

```sh
claude plugin marketplace add https://pancakes.design/claude-plugin/marketplace.json
claude plugin install pancakes@pancakes
```

Inside a Claude Code session, `/plugin marketplace add` and `/plugin install`
take the same arguments. The first time Claude uses a tool that needs your
account, it asks you to sign in to Pancakes (or create a free account) in a
browser window and choose what the agent may do. You can also run `/mcp` and
choose the Pancakes server to sign in ahead of time. You can disconnect it at
any time from Settings, AI assistants, in the Pancakes dashboard.

To get new versions, run `claude plugin marketplace update pancakes`, or turn
on auto-update for the marketplace under Marketplaces in `/plugin`.

In claude.ai, Cowork or Codex, add the plugin from its directory listing once
it is listed. The connector is `https://pancakes.design/mcp`. Agents without
plugin support can add that URL as a remote MCP server; see
https://pancakes.design/agents.

## Skills

| Skill                       | Use it to                                                      |
| --------------------------- | -------------------------------------------------------------- |
| `build-business-website`    | Create a new site from a short interview                       |
| `move-my-website`           | Copy a site you already have into Pancakes                     |
| `update-my-site`            | Change text and photos, undo a change, manage scheduled ones   |
| `update-hours-and-holidays` | Change opening hours, now or for a date range                  |
| `seasonal-refresh`          | Schedule a seasonal menu, offer or banner that ends on its own |
| `weekly-site-checkup`       | Find stale details, broken links and missing information       |
| `connect-a-domain`          | Point a domain you own at the site, or buy one                 |

## Data

The plugin itself stores nothing. The agent sends the site content, images and
instructions you give it to your Pancakes account through
`pancakes.design/mcp`, which records each tool call in your workspace's audit
log. Pancakes' privacy policy is at https://pancakes.design/privacy.
