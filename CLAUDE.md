# CLAUDE.md

This is the website for the band **Bad Valentines** (a five-piece rock band from Helsinki, Finland).

## How to work with the owner

- **The owner is not a programmer.** Use simple, everyday language. Avoid jargon. If a technical word is needed, explain it in one short sentence.
- **Do one thing at a time.** Make one change, explain what you did and how to check it, then wait before moving on to the next thing.
- **Ask before doing anything big or hard to undo**, such as deleting files, changing the site's look across all pages, or publishing (pushing) changes.
- When you finish a change, say plainly **which page** changed and **what visitors will see** differently.

## Secrets and passwords — important

- **Never put passwords, API keys, tokens or any other secrets in the code or in any file in this repository.**
- Secrets belong in **GitHub Secrets** (on GitHub: the repository → Settings → Secrets and variables → Actions). Code should only refer to them by name.
- If you notice a secret in the code, stop and tell the owner straight away, and explain how to move it to GitHub Secrets.
- Public contact details already on the site (such as `media@badvalentines.com`) and public links are fine — they are not secrets.

## What the site is built with

- **Astro** (version 4) — a tool that turns the files in `src/` into a plain, fast website.
- No database, no login, no server code. Every page is a simple static page.
- Visitor statistics come from **GoatCounter** (a small, privacy-friendly counter), loaded in `src/layouts/Base.astro`. Download links on the press kit page use `data-goatcounter-click` labels so downloads are counted.
- Fonts come from Google Fonts: **Bebas Neue** (headings) and **Special Elite** (body text, typewriter style).

## Where things are

| What | File |
|---|---|
| Home page (new single, upcoming gigs, review quote) | `src/pages/index.astro` |
| Music links (Spotify, Tidal, Bandcamp…) | `src/pages/music.astro` |
| Gigs page | `src/pages/gigs.astro` |
| Stories (press reviews and articles) | `src/pages/stories.astro` |
| Press kit / EPK (bio, members, reviews, downloads) | `src/pages/epk.astro` |
| Design reference page (hidden from search engines) | `src/pages/design-system.astro` |
| Shared page frame (head, fonts, statistics script) | `src/layouts/Base.astro` |
| Top menu | `src/components/Nav.astro` |
| Colours, fonts and sizes for the whole site | `public/styles/global.css` |
| Pictures | `public/images/` (press kit pictures in `public/images/epk/`) |
| PDFs (bio, press release) | `public/docs/epk/` |
| Audio files | `public/audio/epk/` |

Each page file in `src/pages/` becomes a web address: `gigs.astro` → `/gigs`, `epk.astro` → `/epk`, and `index.astro` → the front page.

## Common updates and how they are done

- **Gigs on the home page:** edit the `gigs` list at the top of `src/pages/index.astro`. Each gig has a `date`, a `place`, and a `ticketUrl` (use `null` when there is no ticket link yet).
- **Gigs page:** `src/pages/gigs.astro` is written by hand (not from a list). Note: it is separate from the home page list, so the two can get out of sync — check both when gigs change.
- **Pre-save / review links on the home page:** `preSaveUrl` and `reviewUrl` at the top of `src/pages/index.astro`.
- **Press kit content:** the `members`, `reviews` and `downloads` lists at the top of `src/pages/epk.astro`.
- **New picture, PDF or audio file:** put it in the right folder under `public/`, then refer to it with a path starting with `/` (for example `/images/epk/band-photo-vertical.jpg`).
- **Colours:** change them in one place — the `:root` section of `public/styles/global.css`. The pink highlight colour is `--color-highlight`.

## Style rules to keep the site consistent

- Use the colour, font, size and spacing names from `public/styles/global.css` (for example `var(--color-muted)`, `var(--space-lg)`) instead of typing new values.
- Dark background, white text, pink (`#e8185a`) only for highlights and hover effects.
- Content pages are narrow (about 700px wide) and centred.
- Links to other websites open in a new tab and include `target="_blank" rel="noopener noreferrer"`.
- Each page puts its own styling inside a `<style>` block in the same file.

## Trying the site and publishing

- To preview on your own computer: `npm install` (first time only), then `npm run dev`, then open the address it shows (usually http://localhost:4321).
- To check that the site builds without errors: `npm run build`.
- The owner usually edits files directly on GitHub. Only commit or push when the owner asks, and explain what will be published.
