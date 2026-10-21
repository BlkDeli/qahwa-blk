# Qahwa BLK delivery landing page (del.blk.jo)

## What this project is
Static one-page site at del.blk.jo: order tiles for Careem and Talabat plus an embedded branch map. Hosted on GitHub Pages (BlkDeli/qahwa-blk) behind Cloudflare.

## Current state
Live at https://del.blk.jo. Order links are loaded from the Supabase `public.links` table on page load; the hrefs in index.html are only a fallback if the fetch fails. Clicks are logged to `public.clicks`. Map is Google My Maps (mid 1vUmZEhnP0sZ5ezfTDlh0EvX4laJRCuc), embedded zoomed on Amman.

## Decisions made
- Plain index.html, no build step; deploy = push to main.
- Links are edited from the private status page (BlkDeli/qahwa-blk-status, https://blkdeli.github.io/qahwa-blk-status/) via the password-gated `set_link` RPC. Direct writes to `links` are blocked by RLS.
- The embed is shifted up 64px to hide Google's title strip (shows the map owner's profile).
- Keep the fallback hrefs in index.html in sync with the database when links change for good.

## Next steps
1. None pending.

## Log
- 2026-10-21: Replaced Careem link with careem.go.link/2iLRM. Redesigned the page (tiles, map section). Links now editable from the status page.
