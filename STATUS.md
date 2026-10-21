# Qahwa BLK delivery landing page (del.blk.jo)

## What this project is
Static one-page site at del.blk.jo: order tiles for Careem and Talabat plus an embedded branch map. Hosted on GitHub Pages (BlkDeli/qahwa-blk) behind Cloudflare.

## Current state
Live at https://del.blk.jo. Order links are loaded from the Supabase `public.links` table on page load; the hrefs in index.html are only a fallback if the fetch fails. Clicks are logged to `public.clicks`. Find a branch: tap the button, the browser asks for location, and the 41 branches are listed nearest-first with "Hours & map" links that open each branch's Google listing. Branch list is a static copy of the Google My Map (mid 1vUmZEhnP0sZ5ezfTDlh0EvX4laJRCuc) inside index.html (BRANCHES array).

## Decisions made
- Plain index.html, no build step; deploy = push to main.
- Links are edited from the private status page (BlkDeli/qahwa-blk-status, https://blkdeli.github.io/qahwa-blk-status/) via the password-gated `set_link` RPC. Direct writes to `links` are blocked by RLS.
- Look: pure black background, chrome (silver gradient) accents instead of gold, logo shown as white frame only.
- Branches are embedded in the page, not fetched from the map, so the nearest-branch feature works instantly; re-export the map KML and update BRANCHES when branches change.
- Keep the fallback hrefs in index.html in sync with the database when links change for good.

## Next steps
1. Optional: replace name-search links with exact Google listing links per branch (clusters like University St. show a short results list).
2. Refresh the BRANCHES array if the Google My Map changes (Autostrad Zarqa has no coordinates on the map).

## Log
- 2026-10-21: Branch buttons now open the Google listing (hours) via name search at the branch coordinates, not a dropped pin.
- 2026-10-21: Pitch-black + chrome restyle, logo white frame only, replaced embedded map with nearest-branch finder (geolocation).
- 2026-10-21: Replaced Careem link with careem.go.link/2iLRM. Redesigned the page (tiles, map section). Links now editable from the status page.
