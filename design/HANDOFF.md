# Handoff: Foxhole Partners Website

## Overview
A three-page marketing site for **Foxhole Partners**, a senior strategic consultancy founded by Lisa Vedernikova Khanna. The brand is quiet, editorial, and chic — a person's business, not a startup. The typography IS the brand: no logo mark, no icons, no imagery except one portrait photo.

## About the Design Files
The file `Foxhole Partners.dc.html` in this bundle is a **design reference created in HTML** — a prototype showing intended look and behavior, not production code to copy directly. It uses a proprietary component runtime (`support.js`, `<x-dc>`, `{{ }}` template holes, `<sc-if>`/`<sc-for>`); ignore that machinery. Your task is to **recreate the design as a static website** — plain HTML/CSS (or Astro/Eleventy/plain files, whatever is simplest), with real separate pages and real URLs. No JS framework is needed; the only JS in the prototype is page switching, which static routing replaces.

## Fidelity
**High-fidelity.** Recreate pixel-perfectly: exact colors, fonts, sizes, spacing, and copy below. All copy is final — reproduce it verbatim, including punctuation (apostrophes are typographic ', quotes around questions are “curly”).

## Site Structure
Four routes (the nav shows three items; the wordmark links home):
- `/` — Home
- `/what` — What
- `/who` — Who
- `/talk` — Talk

Every "Find a time to talk" button is `mailto:lisa@foxhole.cc` (a scheduler embed may replace the Talk page CTA later — build the CTA as an easily-swappable block).

## Design Tokens

### Colors
- Background (everywhere): deep slate blue `#2c3b46`
- Primary text / headlines: warm cream `#efe6d6`
- Body text (Who page): `#e4dccd`
- Body text (What page): `#cbc3b4`
- Muted text / inactive nav / footer: blue-gray `#93a0a6`
- Accent (labels, "Talk" nav item, italic pull lines): rust `#c47a5d`
- Accent hover: `#d99878`
- Hairline dividers: `rgba(239,230,214,0.16)` (section rules), `rgba(239,230,214,0.12)` (unused now), footer top border `rgba(239,230,214,0.1)`
- CTA underline (rest state): `rgba(239,230,214,0.28)`
- `::selection`: background `#efe6d6`, color `#2c3b46`
- Default link color `#efe6d6`, link hover `#c47a5d`

The palette is exactly three notes — cream, slate blue, rust. Never introduce a fourth color.

### Typography
Google Fonts:
- **Newsreader** (serif) — wordmark, headlines, italic pull lines. Load ital+opsz+wght: 300/400/500 normal, 300/400 italic. Use the optical-size axis (opsz 6..72).
- **Schibsted Grotesk** (sans) — nav, labels, body. Weights 400/500/600.

Font stack fallbacks: `'Newsreader', serif` and `'Schibsted Grotesk', sans-serif`. Apply `-webkit-font-smoothing: antialiased`.

Type styles (all sizes use CSS clamp for fluid scaling):
- Wordmark (nav): Newsreader 400, 21px, letter-spacing -0.01em
- Nav items: Schibsted 12.5px, uppercase, letter-spacing 0.14em
- Page label ("WHAT"/"WHO"/"TALK"): Schibsted 12px, uppercase, letter-spacing 0.2em, color `#c47a5d`
- Home H1: Newsreader 400, `clamp(52px, 12vw, 196px)`, line-height 0.96, letter-spacing -0.025em
- Home tagline: Newsreader italic 300, `clamp(19px, 2.2vw, 27px)`, color `#93a0a6`
- What headline: Newsreader 400, `clamp(30px, 4.6vw, 62px)`, line-height 1.12, letter-spacing -0.015em, max-width 24ch, `text-wrap: balance`
- Question headings: Newsreader italic 300, `clamp(24px, 3.2vw, 38px)`, line-height 1.25, max-width 32ch
- Who H2: Newsreader 400, `clamp(34px, 5vw, 68px)`, line-height 1.04, letter-spacing -0.02em, max-width 16ch
- Talk headline: Newsreader 400, `clamp(28px, 4vw, 54px)`, line-height 1.15, letter-spacing -0.015em, max-width 40ch, `text-wrap: balance`
- Italic accent paragraphs: Newsreader italic 300, rust `#c47a5d`
- Body: Schibsted 400, `clamp(16px, 1.5vw, 19px)` (Who) / `clamp(15.5px, 1.4vw, 17.5px)` (What answers), line-height 1.7
- Footer text: 11.5px, uppercase, letter-spacing 0.16em, color `#93a0a6`

### Spacing
- Global side margin (nav, all mains, footer): `clamp(32px, 12vw, 200px)` — generous, aligned across every page
- Nav vertical padding: 34px
- Page-content top/bottom padding: `clamp(32px, 7vh, 88px)` top, `clamp(40px, 8vh, 96px)` bottom
- Page label → headline gap: `clamp(24px, 4vh, 44px)`
- Content column max-widths: 820px (What sections), 58–60ch (paragraph blocks), 1200px (Who grid), 1100px (Talk)

### CTA button pattern (used on every page)
Not a filled button — an uppercase underlined text link:
- Schibsted 13px, uppercase, letter-spacing 0.14em, color `#efe6d6`
- `padding-bottom: 6px; border-bottom: 1px solid rgba(239,230,214,0.28)`
- Trailing `→` set in Newsreader 16px
- Hover: text and border become `#c47a5d`; transition `.3s ease`
- `display: inline-flex; align-items: center; gap: 10px`

## Screens

### Nav (shared, every page)
Flex row, `justify-content: space-between; align-items: baseline`, padding `34px clamp(32px, 12vw, 200px)`.
- Left: wordmark "Foxhole Partners" (Newsreader 21px, cream, links to `/`). **On the homepage the wordmark is hidden** (opacity 0 in the prototype) since the giant H1 is right below; keep it hidden or omitted on `/` only.
- Right: three items, gap `clamp(22px, 3vw, 40px)`: **What**, **Who**, **Talk**. What/Who are `#93a0a6`, cream on hover and cream when active (current page). **Talk is always rust `#c47a5d`**, hover `#d99878`.

### Home (`/`)
Vertically and horizontally centered column (flex, min-height fills viewport minus nav/footer), text-align center, padding `6vh side 14vh`:
1. H1: `Foxhole<br>Partners` (two lines, clamp up to 196px)
2. Tagline, margin-top `clamp(24px, 4vh, 40px)`: *Every leader needs someone in the foxhole.* (italic, muted `#93a0a6`)
3. CTA "Find a time to talk →" (mailto), margin-top `clamp(30px, 4.5vh, 52px)`
Footer on home: empty (no border, no text) — just breathing room.

### What (`/what`)
Left-aligned editorial column.
1. Label: WHAT
2. Headline (cream, max 24ch): **Foxhole Partners gives you something rare: someone who understands your problems firsthand, has no agenda, and will tell you the truth.**
3. Paragraph (`#cbc3b4`, max 58ch, margin-top `clamp(20px, 3vh, 32px)`): *Our work spans strategy, operations, and communications for companies, campaigns, and causes, and the people who lead them.*
4. Italic rust line (Newsreader italic, `clamp(20px, 2.4vw, 28px)`, margin-top `clamp(24px, 4vh, 40px)`): *Leaders call us with questions like these.*
5. Five question sections (column, gap `clamp(24px, 4vh, 44px)`, max-width 820px, starting margin-top `clamp(28px, 4vh, 44px)`). Each section: 1px top rule `rgba(239,230,214,0.16)`, padding-top `clamp(24px, 4vh, 40px)`; question heading in curly quotes; answer paragraph(s) max-width 60ch, margin-top `clamp(24px, 4vh, 40px)`.

Questions and answers (verbatim):

**"I just stepped into a big job. What should my first 90 days look like?"**
Whether you're stepping into a C-suite role for the first time, taking over a company, or inheriting a team that isn't sure about you yet, the first 90 days set the trajectory for everything that follows. Foxhole Partners helps you structure your listening tour, spot the team dynamics and talent gaps you'll need to navigate, develop your internal and external profile, and build trust with your team, your board, your peers, and the outside world.

**"An important project is stalled. How do I get it moving?"**
Projects and priorities usually stall for ordinary reasons: everyone is at capacity, and the problem doesn't fit neatly into anyone's job. It may need fresh eyes, an outside perspective on a thorny internal situation, or a senior hand your team doesn't have right now. Foxhole Partners takes it on, gets oriented fast, and gets it moving, with the judgment to handle it well and the care to bring your team along on the other side.

**"I've been focused on the work. Now I want people to know about it. Where do I start?"**
Your external presence is part of the job: what you say, where you show up, who you know, and how the outside world understands what you're building. Often the truth is simply that you've been heads-down and your external profile hasn't kept up with where you actually are. Foxhole Partners helps you see which rooms count, which invitations to decline, and what's about to matter before it's obvious to everyone else, and then build and run the presence itself: thought leadership, media, events, speaking, and peer relationships.

**"Something in my organization isn't working. How do I fix it?"**
When something is off in an organization, you usually feel it before you can name it: teams out of sync, projects taking longer than they should, a gap you're not sure whether to hire for or restructure around. Foxhole Partners works alongside your team to figure out what's going on, design the fix, and implement it, in a way that builds trust and leaves the team stronger.

**"I'm in the foxhole. Who's in it with me?"**
Maybe it's a charged product launch that has to land right, an all-hands after a hard stretch, or a crisis that broke an hour ago. Foxhole Partners has been in these moments before, at institutions under genuine threat, alongside leaders who had everything to lose. What you get is someone in the foxhole who has seen it before, will tell you the truth, won't flinch, and will see you through.

6. Closing block (margin-top `clamp(56px, 9vh, 112px)`, top rule, padding-top `clamp(28px, 4vh, 40px)`): CTA "Find a time to talk →".

### Who (`/who`)
1. Label: WHO
2. Two-column grid: `grid-template-columns: minmax(0, 1.5fr) minmax(260px, 1fr); gap: clamp(32px, 6vw, 96px); align-items: start; max-width: 1200px`. (Stack to one column below ~800px; photo after text.)

Left column:
- H2 (max 16ch): **Lisa Vedernikova Khanna is a senior operator and strategic partner to leaders.**
- Two body paragraphs (`#e4dccd`, gap 18px, margin-top `clamp(24px, 4vh, 40px)`, max 58ch):
  - *She served as chief of staff to the chairman of The New York Times, chief of staff at the Democratic National Committee, and policy and communications chief of staff at Instacart.*
  - *She has done this work at some of the most scrutinized institutions in the country, with leaders in their hardest weeks. In every role, she was trusted with the problems that were hard, stuck, or delicate, and she left things better than she found them.*
- Italic rust paragraph (Newsreader italic 300, `clamp(22px, 2.8vw, 32px)`, line-height 1.4, margin-top 18px, max 58ch): *Lisa founded Foxhole Partners because the leaders she worked with all needed the same thing: someone they could trust with everything, who had no agenda and would tell them the truth.*
- Body paragraph (margin-top 18px): *Her colleagues describe her as brutally honest, a velvet heart in an iron glove, and a reliable source of TV show, restaurant, and hot sauce recommendations.*
- CTA "Find a time to talk →", margin-top `clamp(36px, 6vh, 56px)`

Right column:
- Portrait photo, 4:5 aspect ratio, square corners (no border-radius), `object-fit: cover`. Asset to be supplied by the client — use a plain placeholder block until then.
- Caption under photo (margin-top 12px): "LISA VEDERNIKOVA KHANNA" — 11.5px, uppercase, letter-spacing 0.14em, `#93a0a6`
- Reserved for later: one named quote may be added below the founding paragraph, set alone in white space. Don't render it empty; just don't design it out.

### Talk (`/talk`)
Vertically centered column (flex, `justify-content: center`), max-width 1100px, bottom padding `clamp(64px, 12vh, 140px)`:
1. Label: TALK
2. Headline (max 40ch): **The first conversation is for us to figure out what's keeping you up at night, and what we can do about it.**
3. CTA "Find a time to talk →" (mailto), margin-top `clamp(36px, 6vh, 56px)`
Future: an inline scheduler embed (Calendly or Cal.com, embedded — not an outbound link) will replace the mailto here.

### Footer (shared, non-home pages)
Padding `clamp(24px, 4vh, 40px) clamp(32px, 12vw, 200px)`, 1px top border `rgba(239,230,214,0.1)`, flex space-between:
- Left: "FOXHOLE PARTNERS" (11.5px uppercase, `#93a0a6`)
- Right: nothing (deliberately no email in footer)
Home page: footer area exists as spacing only — no border, no text.

## Interactions & Behavior
- Nav links: color transition `.25s ease`; active page item is cream
- CTA links: color + border-color transition `.3s ease`
- No animations, no scroll effects, no motion beyond hovers — the site is deliberately still
- All "Find a time to talk" CTAs and the Talk nav destination CTA: `mailto:lisa@foxhole.cc`

## Voice rules (for any copy edits)
- "Foxhole Partners" or "us/we" as the actor per existing copy — never invent new first-person singular; the one "I" (none currently on page) is deliberate when it appears
- No jargon, no filler; the copy above is final

## What to Avoid
Rounded/filled colorful buttons, corporate blue, gradients, icons, stock photography, emoji, cards/boxes (use hairline rules instead), anything that reads tech-startup or coaching-business.

## SEO / head
- Title: "Foxhole Partners" (home), "What — Foxhole Partners", etc.
- Meta description suggestion: "Foxhole Partners is a senior strategic consultancy for leaders — strategy, operations, and communications for companies, campaigns, and causes."
- Set `<meta name="theme-color" content="#2c3b46">`
- Preconnect to fonts.googleapis.com / fonts.gstatic.com

## Files
- `Foxhole Partners.dc.html` — the full design reference (markup, styles inline, all copy in the script block at the bottom)
