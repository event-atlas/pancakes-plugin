---
name: connect-a-domain
description: Connect a custom domain to a Pancakes website or help the person get one. Use when the person mentions a domain, a web address, www, DNS, or moving their address from another host.
---

# Connect a domain

Domains are set up in the Pancakes dashboard, not through the connector,
because they involve DNS records at another company and, for a new domain, a
purchase the person makes themselves.

1. Call `list_sites` and `get_site` to find the site and its current public
   address.
2. Send the person to the site's Domains page in the Pancakes dashboard:
   the site's `dashboardUrl` from `get_site` followed by `/domains`.
3. Explain the two paths there:
   - A domain they already own: Pancakes shows the DNS records to add at their
     registrar and checks them automatically.
   - A new domain: they can search for and buy one on the same page.
4. Offer to wait while they do it and to check the site afterwards with
   `preview_site`.

Never ask the person for registrar passwords or account details.
