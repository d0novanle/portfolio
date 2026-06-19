# Donovan Le — Portfolio

A personal design portfolio for Donovan Le (2025 UCSD grad, B.S. Design & HCI; Lead Human Factors Designer & Researcher at the Contextual Robotics Institute). Mid-century-modern / Blue Note records aesthetic. Built as a **static site** — plain HTML/CSS/JS, no build step, no CMS. Content is edited directly in the code.

---

## Current State

- ✅ **Landing page** — vinyl-crate grid of album covers, built and iterated.
- ✅ **BySage case study** — fully built with real content and real images. **This is the reference template** for the other four case studies.
- ⏭️ **Next** — replicate the BySage structure for Input Matters, Kaibigang Pilipino, ACM at UCSD, and NexGen, then add About / Reviews / Contact.

---

## File Structure

```
portfolio/
├── preview.html          ← the entire site (landing + case study), content inline
└── images/
    ├── bysage-splash.jpg          (case study splash composite — homepage, cart, product page)
    ├── bysage-architecture.jpg    (site map diagram)
    ├── bysage-product-m1.jpg      (mobile product page — top half)
    ├── bysage-product-m2.jpg      (mobile product page — bottom half)
    ├── bysage-laptop.jpg          (desktop homepage)
    └── bysage-about.jpg           (about-us brand timeline, cropped)
```

> Rename `preview.html` to `index.html` when you deploy (hosts expect `index.html` as the entry point).

---

## Aesthetic

Mid-century modern / Blue Note records (Reid Miles), ELAC-turntable-manual influence.

- **ELAC orange** `#E0792B` · **Blue Note red-orange** `#C2391F` · **Cream paper** `#F4ECDC` · **Cream deep** `#EBE0CA` · **Warm near-black ink** `#1A1714` · **Green splash** `#14402C`
- Divider/border grey: `--paper-line` = `rgba(26,23,20,.12)` (flattened ≈ `#DCD5C5`)
- Display font: **Oswald** (condensed caps). Body: **Spectral** (serif). Subtle paper-grain overlay.
- **WCAG 2.1 AA**: focus-visible, contrast, prefers-reduced-motion, keyboard nav, skip link.

---

## Landing Page

- **Hero** — left-aligned, compact (kept short so the grid is visible on load). Copy: *"Hi, I'm Donovan, a Human-Centered Product Designer who still enjoys analog modalities — vinyl records, film photography, & vintage fashion — in a modern world."* with colored keyword highlights, then "Browse my shelf:" on its own line.
- **Album grid** — responsive, max 3 per row (→ 2 → 1 on smaller screens). Sleeves are size-capped (~340px) and centered.
- **Card interaction** — the cover is a static frame; on hover/focus a **vinyl record slides out to the right** (enlarged colored label + concentric grooves masked to the black vinyl only). Click → routes to that case study page.
- **Under each cover** — title, role (italic), and a one-sentence pitch line.

---

## Case Study Page (BySage = the template)

**Splash (Brandon-Lee-style layout):** a full-bleed image band on top, then the big display **title + one-sentence tagline** below it on cream, then the meta row. (Tagline pattern: *"Created [what] for [who] to [outcome]"* — impact-first, one sentence, no metric.)

**Two-column body:**
- **Meta row** — Role · Team · Skills · Timeline · Client (team members each on their own row).
- **Sticky left nav** with a **turntable graphic** whose **tonearm sweeps inward continuously as you scroll**, landing on the grooves at the marked spot exactly when the last section becomes active. Section links **smooth-scroll** and **highlight** (orange dot + red text + scale) as you pass them. Only sections with content appear (driven by `done:true` in the `SECTIONS` array).

**Image treatment:**
- Wide/desktop screenshots → full content-width.
- Tall mobile screenshots → constrained phone-width, centered.
- A long mobile screen can be **split into two halves shown side by side** so it doesn't run long.

**BySage section flow (8 sections — clone this for the others):**
Overview → Research → Defining the Brand → Architecture → Final Design → Testing → Results → Reflection.

---

## Content Rules

- **Role framing:** Donovan is the **lead** (Lead Product Designer & Researcher). Team: **Caitlyn Cielo (PM) · Mark Morera · Ryan Eang**.
- **Metrics (BySage):** 200% increase in Instagram followers · Spring 2024 collection sold out in 3 minutes · 20%+ increase in traffic during drops.
- **Testimonial:** excerpt from Cameron Pitel's (founder) recommendation letter, in the Results section.
- Minimal case studies — overview + real metrics only; `[brackets]` for anything not yet written.

---

## The Five Records (BN-2401…05)

| # | Project | Role | Notes |
|---|---------|------|-------|
| BN-2401 | Input Matters (Contextual Robotics) | Human Factors Designer & Researcher | Teleoperation interfaces; HRI 2026 co-authored paper |
| BN-2402 | **BySage** | Lead Product Designer & Researcher | Drop-based streetwear → year-round site. **Built — reference template.** |
| BN-2403 | Kaibigang Pilipino | Head of Design | Membership portal + gamified attendance |
| BN-2404 | ACM at UCSD | UX Designer | Design systems (2,000+ members) |
| BN-2405 | NexGen | `[Role]` | Startup/client; placeholders |

---

## Other Sections (to add)

- **About** — 3+ yrs experience, bio, philosophy, skills, awards (Design Co. 3rd place 2023; USC CreateSC finalist 2024).
- **Reviews** — placeholder quotes.
- **Contact** — LinkedIn (`linkedin.com/in/donovan-le/`) + portfolio only; no email/phone.

---

## Editing Content

All content lives inline in `preview.html` in two JS objects near the bottom `<script>`:
- **`PROJECTS`** — the album cards (id, catalog #, title, role, label color, cover art, pitch).
- **`SECTIONS`** — the case-study sections. Each has a `done` flag — only `done:true` sections show in the nav, get a tonearm stop, and render. Flip the flag to reveal a section.

Keep images **referenced** (`<img src="images/...">`), never base64-embedded — that keeps the file small and fast. Add `loading="lazy"` to below-the-fold images.

---

## How to Host This — Step by Step

You have three options, simplest first. **You do NOT need Vercel just to preview** — the Live Preview extension covers that. You need a host (GitHub Pages or Vercel) only when you want a public URL anyone can visit.

### Option A — Preview locally in Cursor (no hosting, what you're doing now)
1. Open the project folder in Cursor.
2. Install the **Live Preview** extension (Extensions panel → search "Live Preview" by Microsoft).
3. Right-click `preview.html` → **Show Preview**, or open it and click the preview icon. For the most accurate rendering (hover, scroll, tonearm), use **"Show Preview (External Browser)."**
4. Edit + save → the preview auto-reloads. This is local only — no public URL.

### Option B — Publish a public URL with GitHub Pages (free, simplest hosting)
1. Rename `preview.html` → **`index.html`**.
2. In Cursor's Source Control panel (or terminal), initialize a repo and push:
   ```bash
   git init
   git add .
   git commit -m "Initial portfolio"
   ```
3. On github.com, create a new repository (e.g. `portfolio`). Copy the commands GitHub shows under "…or push an existing repository," which look like:
   ```bash
   git remote add origin https://github.com/<your-username>/portfolio.git
   git branch -M main
   git push -u origin main
   ```
4. On GitHub: repo → **Settings** → **Pages** → under "Build and deployment," set **Source: Deploy from a branch**, **Branch: main / root** → Save.
5. Wait ~1 minute. Your site is live at `https://<your-username>.github.io/portfolio/`.
6. To update later: edit in Cursor → `git add .` → `git commit -m "update"` → `git push`. The site redeploys automatically.

### Option C — Publish with Vercel (also free; nicer URLs + instant redeploys)
Only worth it over Pages if you want a custom domain or faster deploys. Requires the repo from Option B first.
1. Push your repo to GitHub (steps 1–3 above).
2. Go to **vercel.com** → sign in with GitHub → **Add New… → Project** → import your `portfolio` repo.
3. Framework Preset: **Other** (it's a static site — no build command, no output dir needed). Click **Deploy**.
4. You get a live URL like `https://portfolio-<you>.vercel.app`. Every `git push` auto-redeploys.

### Which should you pick?
- **Just iterating privately?** Option A (Live Preview) — you're already set.
- **Want a shareable link with the least setup?** Option B (GitHub Pages).
- **Want a custom domain / fastest deploys?** Option C (Vercel).

> Note: GitHub Pages serves from a subpath (`/portfolio/`). Because every image here is referenced with a **relative** path (`images/...`), it works on Pages, Vercel, and locally without changes. Keep paths relative and you won't hit broken images.

---

## How to Pick This Back Up (new session)

1. Open `preview.html` in Cursor, run Live Preview.
2. To add a case study: duplicate the BySage `view-case` block, fill each section with real content, add its entries to `SECTIONS` (`done:true`), drop images into `/images`, reference them with `loading="lazy"`.
3. To change which sections show: flip `done` flags in `SECTIONS` — nav + tonearm update automatically.
4. Optimize/resize images before adding; split long mobile screenshots into halves for a side-by-side row.
