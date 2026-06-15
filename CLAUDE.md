# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Novi Sad Relational Tech (NSRT) — community tools crafted by, with, and for Novi Sad residents. Part of [NSRelaTech](https://github.com/NSRelaTech), the Novi Sad chapter of [Citizen Infrastructure](https://github.com/Citizen-Infra).

**Live site:** [nsrt.netlify.app](https://nsrt.netlify.app)
**Telegram:** [t.me/NSRelaTech](https://t.me/NSRelaTech)
**Luma calendar:** [lu.ma/nsrt](https://lu.ma/nsrt)

## Commands

```bash
# Deploy to Netlify (deploys current directory as-is, no build step)
npx netlify deploy --prod --dir=.

# Generate OG image (requires Node.js and Puppeteer)
npm install
node generate-og-image.js
```

The OG image script uses Puppeteer to screenshot `og-image.html` at 1200x630 and saves to `og-image.png`.

## Architecture

Static landing page with no build step — just `index.html` served directly by Netlify.

**Trilingual support (EN/SR/RU):**
- Language toggle buttons in top-right corner
- Content elements have `data-lang="en|sr|ru"` attributes
- CSS shows/hides content based on `body.sr` or `body.ru` class (EN is the default — no class on body)
- Preference saved to localStorage (`nsrt-lang`)
- Auto-detects browser language on first visit
- When adding new content, always provide all three language variants
- For dynamically inserted HTML, call `setLang(currentLang)` after DOM update to re-apply visibility

**Key CSS patterns:**
```css
[data-lang="sr"], [data-lang="ru"] { display: none !important; }
body.sr [data-lang="en"], body.sr [data-lang="ru"] { display: none !important; }
body.sr [data-lang="sr"] { display: block !important; }
```

**Dynamic events (Section 01):**
- Fetches upcoming events from `scenius-digest.vercel.app/api/events?community=nsrt`
- This API aggregates Luma links from the NSRT Telegram group's Events topic + the `lu.ma/nsrt` calendar
- Events are filtered to future-only and sorted by date
- Graceful fallback: shows link to lu.ma/nsrt if API fails, "no events" message with Telegram link if empty

**Page sections:** Events (01), Tools (02), Ideas (03), Suggest (04), Manifesto, Footer.

**Design system:** Navy/amber/cream palette with blueprint grid background. Fonts: Libre Baskerville (display), Source Serif 4 (body), JetBrains Mono (UI/mono). CSS variables defined in `:root`.

## Related Projects

| Project | Description |
|---------|-------------|
| [dear-neighbors](https://github.com/NSRelaTech/dear-neighbors) | Chrome extension — neighborhood dashboard (fork for NS collaboration) |
| [my-community](https://github.com/Citizen-Infra/my-community) | Chrome extension — community dashboard with Bluesky |
| [community-admin](https://github.com/Citizen-Infra/community-admin) | Admin platform for organizers (WIP) |
| [scenius-digest](../../scenius-digest/) | Provides the events API — monitors NSRT Telegram group and Luma calendar |
| [meetups](https://github.com/NSRelaTech/meetups) | NSRT community meetup materials — decks, session briefs, planning docs |

## Design Principles

- **Neighbor-to-neighbor, not citizen-to-government.** Strengthen bonds between residents, not reporting tools for authorities.
- **Village-scale, not city-scale.** Scope tools to a block, building, or mesna zajednica.
- **Interoperable small tools over one platform.** Use shared feed formats so tools can publish and consume local data independently.
- **Remix, don't reinvent.** Adapt existing [RTP patterns](https://www.relationaltechproject.org/remix) to Novi Sad's context.
- **Pedagogical by design.** Every interaction should teach users to think collectively.
- **Sovereignty-preserving.** Communities maintain control over their tools and data.
