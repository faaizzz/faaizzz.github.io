# CLAUDE.md

This file provides context for AI assistants working with this codebase.

## Project Overview

This is a static personal portfolio website for **Faaiz K Rissad**, a .NET Full Stack Azure Cloud Developer. It is a single-page application (SPA) hosted on GitHub Pages at `faaizzz.github.io`.

The site is based on the **Super Folio** template by [TemplateFlip](https://templateflip.com/) (free variant). All customization is applied directly to the template files.

## Repository Structure

```
faaizzz.github.io/
├── index.html          # The entire website — single HTML file containing all sections
├── favicon.ico         # Site favicon
├── css/
│   ├── main.css        # Custom styles (the only CSS file to edit for design changes)
│   ├── bootstrap.min.css          # Bootstrap 5 framework
│   ├── aos.css                    # Animate On Scroll library styles
│   ├── bootstrap-icons/           # Bootstrap Icons icon font
│   └── font-awesome/              # Font Awesome 5 icon library
├── scripts/
│   ├── main.js                    # Custom JavaScript (the only JS file to edit for behavior)
│   ├── bootstrap.bundle.min.js    # Bootstrap 5 JS bundle (includes Popper)
│   ├── aos.min.js                 # Animate On Scroll library
│   ├── masonry.pkgd.min.js        # Masonry layout for portfolio grid
│   ├── imagesloaded.pkgd.min.js   # Prerequisite for Masonry
│   ├── BigPicture.min.js          # Lightbox/fullscreen viewer for portfolio images
│   └── purecounter.min.js         # Animated number counter (loaded but not currently used)
├── images/
│   ├── avatar.jpg / avatar1.jpg   # Profile photos
│   ├── wave-bg.svg                # Decorative wave background in hero section
│   ├── marker.svg                 # Decorative underline marker used on section headings
│   ├── illustrations/             # SVG hero/section illustrations
│   ├── services/                  # SVG service icons (web-design, full-stack, ui-ux, etc.)
│   ├── portfolio/                 # Portfolio project images (full + small thumbnail versions)
│   ├── testimonials/              # Client headshot photos
│   ├── team/                      # Team member photos
│   └── clients/                   # Client/company logos
├── README.txt          # Original template usage instructions
└── LICENSE-free.txt    # Template license
```

## Technology Stack

| Library | Version | Purpose |
|---|---|---|
| Bootstrap | 5.x | Responsive grid, components, utilities |
| Font Awesome | 5.x | Social and general icons (`fab`, `fas` classes) |
| Bootstrap Icons | 1.x | Additional icon set |
| AOS | — | Scroll-triggered entrance animations |
| Masonry.js | — | Pinterest-style portfolio grid layout |
| BigPicture.js | — | Lightbox viewer for portfolio images |
| imagesLoaded | — | Fires callback after all images load (used with Masonry) |
| PureCounter.js | — | Animated number counters (available but not wired up) |
| Nunito Sans | Google Fonts | Primary typeface (300, 400, 700, 800 weights) |

No build tools, package managers, or frameworks are used. This is plain HTML/CSS/JS.

## Page Sections (in order)

All sections live inside `index.html` as sequential `<div>` blocks with anchor IDs:

1. **`#top`** — `<body id="top">` — scroll-to-top target
2. **Navbar** — `#header-nav` — sticky on scroll, links to all sections
3. **Hero** — `<header>` inside `#content` — intro with name, title, social links, CTA button
4. **`#about`** — bio text, personal details table, avatar photo
5. **`#services`** — 4-column icon grid (Front End, Back End, Cloud, Database)
6. **`#skills`** — Bootstrap progress bars showing proficiency percentages
7. **`#portfolio`** — Masonry grid of 8 portfolio items with BigPicture lightbox
8. **`#experience`** — 4 Bootstrap cards with job/role history
9. **`#testimonials`** — 4 client quote blocks
10. **`#contact`** — Contact form (Formspree), contact details sidebar
11. **Footer** — name, tagline, social links, copyright
12. **`#scrolltop`** — floating scroll-to-top button (appears after scrolling down)

## Key Conventions

### HTML
- Template version is `1.2.0` — all asset URLs include `?ver=1.2.0` cache-buster query strings.
- AOS animations use `data-aos` and `data-aos-delay` attributes directly on elements.
- Portfolio lightbox uses `data-bp` attribute on `<img>` tags within `.bp-gallery`.
- Section containers alternate between `.container` (full Bootstrap width) and `.container-narrow` (custom max-width: 1024px).

### CSS (`css/main.css`)
- This is the **only CSS file to modify** for custom styling. Do not edit vendor CSS files.
- Key custom utility classes:
  - `.container-narrow` — max-width 1024px centered container
  - `.marker` / `.marker-center` — decorative SVG underline on headings (via `::after` pseudo-element)
  - `.hover-effect` — subtle translateY(-2px) lift on hover
  - `.text-small` — `0.875rem` font size
  - `.wave-bg` — animated SVG wave at the bottom of the hero section
  - `.section` — adds `scroll-margin-top: 2rem` for correct anchor scroll offset
- Responsive breakpoints follow Bootstrap conventions (`48em` / 768px).
- Reduced motion: AOS animations are suppressed via `prefers-reduced-motion` media query.

### JavaScript (`scripts/main.js`)
- Wrapped in an IIFE with `"use strict"`.
- **AOS** is initialized on `window.load` with `once: true` and `disable: 'mobile'`.
- **Navbar** becomes sticky (`fixed-top`) after any scroll and adds `shadow-sm`.
- **Masonry** initializes only when `.grid` element exists on the page.
- **BigPicture** lightbox:
  - Elements with `[data-bigpicture]` attribute open arbitrary media (image/video).
  - All `.bp-gallery a` links open a navigable gallery; the anchor `href` becomes the caption link in fullscreen view.
- Custom code should be added at the bottom of the IIFE, after the `// Add your javascript here` comment.

## Development Workflow

### Previewing Changes
No build step required. Open `index.html` directly in a browser, or serve locally:
```bash
# Python 3
python3 -m http.server 8080
# Then open http://localhost:8080
```

### Making Content Changes
- **Text/bio/contact info**: Edit the relevant section in `index.html`.
- **Skills**: Update `style="width: X%"` and `aria-valuenow="X"` on `.progress-bar` elements in `#skills`.
- **Portfolio items**: Replace images in `images/portfolio/` and update `<img src>` and `<a href>` in `#portfolio`.
- **Social links**: Update `href` on `<a>` tags in the hero `.social-nav` and footer `.social-nav`.
- **Contact form**: Replace `https://formspree.io/your@email.com` with a real Formspree endpoint.
- **Page title / site name**: Update `<title>` in `<head>` and `.site-title` link text in the navbar.

### Making Style Changes
- All custom styles go in `css/main.css`.
- Bootstrap utility classes (`bg-light`, `text-muted`, `fw-bolder`, etc.) can be used directly in HTML.

### Deploying
Push to the `master` or `main` branch — GitHub Pages automatically serves from the repository root.

## Known Issues / Notes

- The contact section's right-column contact details still contain **template placeholder values** (`walter@company.com`, `username@skype.com`, `+0718-111-0011`) that should be updated to real info.
- The footer still references the **template author name "Walter Patterson"** and template social links — these should be updated to Faaiz's details.
- Some experience and testimonials sections contain **boilerplate lorem-ipsum-style content** that should be replaced with real experience/testimonials.
- `purecounter.min.js` is loaded but no counter elements (`data-purecounter-*`) exist in the HTML — it can be removed if not needed, or used to add animated stats.
- Portfolio grid items currently link to generic external sites (Dribbble, GitHub, SoundCloud, etc.) rather than actual projects.

## Branch Strategy

- **`master`** / **`main`**: Production branch — served live by GitHub Pages.
- Feature branches should be merged to `main`/`master` via pull requests.
