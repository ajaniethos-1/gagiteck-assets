README.txt
─────────────────────────────────────────────────────────────
Gagiteck.com robots.txt Configuration
─────────────────────────────────────────────────────────────

Purpose:
This repository contains the official robots.txt file for Gagiteck.com,
a site hosted on the GoHighLevel (GHL) platform. The file is optimized
for search engine indexing and AI platform visibility, including GPTBot,
ClaudeBot, PerplexityBot, and other semantic crawlers.

─────────────────────────────────────────────────────────────
File Location:
- robots.txt is located in the root directory of this repository.

─────────────────────────────────────────────────────────────
Hosting Instructions:

Since GHL does not support root-level file uploads, this file must be
served externally and proxied to https://www.gagiteck.com/robots.txt.

Option A: GitHub Pages
1. Enable GitHub Pages in repository settings.
2. Set source to the main branch and root folder.
3. GitHub will serve the file at:
   https://gagiteck.github.io/robots.txt

Option B: Cloudflare Worker Proxy
Use a Cloudflare Worker to redirect requests from:
   https://www.gagiteck.com/robots.txt
to:
   https://gagiteck.github.io/robots.txt

Example Worker Script:
─────────────────────────────────────────────────────────────
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const url = new URL(request.url)
  if (url.pathname === '/robots.txt') {
    return fetch('https://gagiteck.github.io/robots.txt')
  }
  return fetch(request)
}
─────────────────────────────────────────────────────────────

─────────────────────────────────────────────────────────────
Verification:
Use Google Search Console to verify:
- robots.txt accessibility
- Disallowed paths
- Sitemap declaration

─────────────────────────────────────────────────────────────
Maintenance:
- Update disallowed paths as GHL evolves
- Keep sitemap URL current
- Monitor crawl behavior and AI indexing performance

─────────────────────────────────────────────────────────────
Contact:
For technical questions or updates, contact the Gagiteck SEO team.

─────────────────────────────────────────────────────────────
