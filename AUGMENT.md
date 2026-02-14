# AUGMENT.md — Brainstorming & Vision

This document captures brainstorming sessions and long-term vision for maximebories.com. Referenced from CLAUDE.md for continuity across sessions.

---

## Dashboard / Public Presence — Brainstorm (Feb 2026)

### Context
Exploring the idea of expanding the site beyond a static portfolio into a living, public dashboard — a space to share what I care about, not just what I've done.

### Directions Considered

#### 1. "Now" page
- What I'm working on, reading, learning, thinking about
- Updated manually or semi-automatically
- Sections: "Currently building", "Reading", "Listening to", "Exploring"
- Low maintenance, high personality
- See nownownow.com for the movement

#### 2. Living dashboard (data-driven)
- Pulls real data: GitHub activity, blog posts, Spotify, books read, project status
- Visualizations: contribution heatmaps, tech stack radar, project timelines
- APIs: GitHub, Goodreads, Last.fm, etc.
- Higher maintenance but technically impressive

#### 3. Digital garden
- Not a blog (linear, chronological) — a garden (interconnected, evolving notes)
- Ideas at various stages: seedlings, budding, evergreen
- Topics: embedded systems, signal processing, open source, design
- Links between notes create a knowledge web
- Tools: Obsidian-style backlinks, tag-based navigation

#### 4. Opinionated "uses/likes/thinks" page
- Dev setup, tools, hardware
- Opinions on tech (languages, frameworks, practices)
- Recommendations (books, talks, repos)
- Shows personality without requiring constant updates

#### 5. Hybrid: personal API
- A single `/dashboard` page that aggregates everything
- Sections: pinned projects, latest blog post, current status, recent reads, GitHub stats
- Digital identity in one glance

### Unique Angles (from background)
My profile (embedded systems, FPGA, DSP, signal processing) opens content that most web devs can't produce:
- **Hardware builds** — photos, schematics, board layouts
- **Signal visualizations** — spectrograms, waveforms, constellation diagrams
- **Technical deep-dives** — niche knowledge that's genuinely rare online
- **Bridging hardware and software** — a unique perspective few people share publicly

### Blogging: Technical Decision
- **Astro** identified as the best migration path from current pure HTML
- Minimal friction: existing `index.html` becomes `src/pages/index.astro` (near copy-paste)
- Static assets move to `public/` (CSS, fonts, icons — untouched)
- Blog posts are Markdown files with frontmatter in `src/content/blog/`
- Output is still static HTML — same performance, same GitHub Pages hosting
- Deployment switches from branch-based to GitHub Actions (`withastro/action`)
- RSS feed comes free with `@astrojs/rss`
- Migration estimated at ~30 minutes for the scaffold

---

## Photo Portfolio — Brainstorm (Feb 2026)

A dedicated space to showcase photography work. Could be a separate page (`/photos`) or integrated into a broader creative portfolio.

### Considerations
- Gallery layout: masonry grid, lightbox on click, or full-bleed scroll
- Categories/tags: landscape, street, architecture, abstract, etc.
- Image hosting: self-hosted in repo (heavy on git), or external (Cloudinary, imgix, S3)
- Lazy loading for performance
- EXIF metadata display (camera, lens, settings) — optional but adds depth
- Minimal captions vs. narrative context per photo
- Print/download options?

### Technical Options
- Pure CSS grid masonry (current stack, no JS)
- `<dialog>` element for native lightbox (no library)
- `srcset` / `<picture>` for responsive image sizes
- WebP/AVIF with fallbacks for compression
- If Astro migration happens, image optimization comes built-in (`astro:assets`)

---

## Digital Design Portfolio — Brainstorm (Feb 2026)

A space to showcase visual/creative work: UI designs, branding, typography experiments, layout explorations, digital illustrations, motion design.

### Considerations
- Project-based layout: each piece as a case study card with title, thumbnail, and description
- Categories: UI/UX, branding, typography, illustration, motion/animation
- Interactive previews where possible (embedded CSS animations, SVG demos, before/after)
- Process shots: not just the final result, show the thinking (sketches, iterations, tooling)
- Tool callouts: Figma, Illustrator, CSS, Blender, etc.
- Could merge with photo portfolio into a unified `/gallery` or `/creative` page, or keep separate

### Technical Options
- Same card grid layout as recommendations page (`.reco-grid` pattern already exists)
- Larger cards with thumbnail images for visual work
- Lightbox/modal for full-size previews
- Possible hover effects: reveal description overlay, subtle zoom
- Video/GIF embeds for motion work (self-hosted, autoplay muted)

---

### Open Questions
- What do I actually want to share? (journey, opinions, curated resources, project showcases, all of the above?)
- How much automation vs. manual curation?
- Blog vs. digital garden vs. both?
- Dashboard as a section of the main page or a separate route (`/dashboard`)?
- Photo portfolio: separate page or part of a broader creative section?
- Digital design: case-study format or simple gallery?
- Unified `/creative` page combining photos + design, or keep them distinct?
