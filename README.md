# DR. DREY — Music Player

Standalone single-file music player. Plays live DR. DREY tracks from `drdrey.com/audio/*.mp3` + matching cover art.

## What this is

A focused portfolio/showcase player built for challenge #8 of the Drey Tools buildout. Complements (does not replace) the existing drdrey.com NowPlaying full-screen mode — this is a tighter, single-screen layout meant to be embeddable or deployable as its own domain.

## What it has

- Album art with floating animation + soft color-glow from the cover
- Play / pause / prev / next / shuffle / repeat (off/all/one)
- Scrubbable progress bar with cyan thumb
- Volume slider
- Like button (session-only)
- Keyboard shortcuts: space = play/pause, left/right arrows = prev/next
- Media Session API (lock-screen + system media controls)
- Up Next queue (10 tracks, click to jump)
- Warm-dark theme with cyan (matches Drey brand)
- Mobile-safe viewport (100dvh), responsive up to 480px

## How to run

```bash
open index.html
```

That's it. No build step, no dependencies. Pure HTML + CSS + vanilla JS.

## How to deploy

Drop the folder on any static host. Options:

```bash
# Option A: Cloudflare Pages (recommended per Drey's hosting rule for static)
wrangler pages deploy . --project-name dreytools-player --branch main

# Option B: Vercel static (if folding into drdrey.com)
vercel --prod
```

**Suggested domain:** `player.dreytools.com`

## Tracks loaded

Uses 10 live tracks from drdrey.com across 5 albums (Midnight Manual, 4AM, No Apologies EP, 3, Dark Mode). To change the setlist, edit the `TRACKS` array near the top of the script block in `index.html`.

## Decisions to make before shipping to prod

1. **Where does this live?** Standalone at `player.dreytools.com` as a portfolio piece, or fold into drdrey.com as an alternate `/classic-player` route?
2. **Source of truth for tracks** — currently hardcoded. Could fetch from a JSON manifest at drdrey.com for auto-sync.
3. **Replace NowPlaying?** — This is simpler than the current NowPlaying screen on drdrey.com. Decide if it's a demo piece or a real swap.

## Deployed

**Live URL:** https://dreytools-player.pages.dev

**Target custom domain:** player.dreytools.com (needs DNS CNAME — requires CF API token wrangler doesn't expose)

## Purpose — why this exists alongside drdrey.com

drdrey.com already ships a far more advanced player (3D hero orb, waveform, full NowPlaying mode, theme engine). This is the **simpler, single-file** companion:

- Portfolio showcase piece under dreytools
- Potential embeddable widget for blogs/sites
- Funnels traffic back to drdrey.com via the footer link

## Changelog

- **2026-04-17**: Initial build + deploy to Cloudflare Pages (dreytools-player.pages.dev). Single-file HTML. 10 tracks wired to drdrey.com. Added "Full experience on drdrey.com" footer link. Awaiting custom domain wiring to player.dreytools.com.
