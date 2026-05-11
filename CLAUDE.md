# CLAUDE.md — Cole Dudley · Personal Portfolio

This file is the persistent context for any Claude session working on Cole Dudley's personal portfolio. Read it first. Update it as the project evolves.

This is **distinct from 2nd Life Cycles** (the bike restoration brand at `~/website42whlstls/`). 2nd Life is a shop. This site is Cole, the maker — built for apprenticeships, residencies, and public art applications.

---

## 1. Goals (in priority order)

1. **Speed.** Most reviewers will skim on a phone. Page weight under 1 MB on first load. Images optimized.
2. **Easy contact.** Phone and email tappable, contact button in nav, contact section as the closing beat.
3. **Image-forward presentation.** The work leads. Type and color stay quiet so photos punch.
4. **Personal, handmade, professional.** Not corporate, not twee. Confident but reserved.

## 2. Sections (single-page scroll)

| # | Anchor | Purpose |
|---|---|---|
| 1 | `#top` | Hero: name, one-line intro, contact CTA |
| 2 | `#about` | Who Cole is + what opportunities he's open to |
| 3 | `#work` | Selected Work — 2 functional-art pieces (SewCycle installation) + 4 prints |
| 4 | `#posters` | Posters & Flyers — event/commission flyer samples |
| 5 | `#gallery` | Bike Gallery — restoration/build photos |
| 6 | `#contact` | Phone, email, prominent mailto button |

## 3. Design system — "SoCal Quiet"

### Typography
Single family: **Figtree** (Google Fonts). Used quietly here — display weight reserved for hero and section headers; body sits at 400/500. No second typeface.

### Palette
Inspired by the dry hills above LA: bone-pale grasses, sage scrub, terracotta soil. Quieter than the 2nd Life Cycles palette so photos lead.

```css
:root {
  --bone:      #F2EEE5;  /* sun-bleached background */
  --shell:     #E8E1D3;  /* subtle inset / placeholder fill */
  --ink:       #1F2421;  /* warm charcoal text */
  --ink-soft:  #5A5F5B;  /* secondary text, captions */
  --sage:      #8A9684;  /* primary quiet accent (chaparral) */
  --clay:      #B86F4E;  /* warm CTA accent (dried poppy) */
}
```

**Rules:**
- Bone is the only background. No alternating dark/light sections — it competes with the photos.
- Sage is the rule-line / quiet-accent color (dividers, eyebrows, hover).
- Clay is reserved for the contact CTA and one or two highlight moments. Never body copy.
- Don't introduce new colors without updating this file.

### Layout
- Mobile-first. Content column max-width: 720px (tablet), 920px (desktop) for the gallery grid.
- Generous whitespace. Section padding 80px desktop / 56px mobile.
- No torn-paper dividers. Just thin sage rules or whitespace.

## 4. Asset conventions

**Layout:**

```
assets/
├── portfolio/
│   ├── bike/      portfolio-bike-NN.jpg    (2 files — installation/functional-art photos, 4:5 portrait crop)
│   ├── print/     portfolio-print-NN.jpg   (4 files — flat scans, natural aspect, no crop)
│   └── posters/   poster-NN.jpg            (3+ files — flyers/event posters, natural aspect)
└── gallery/
    └── bikes/     gallery-NN.webp          (6+ files — square 1:1)
```

**Format choice:**
- Photos with broad gradients (bikes, installations) compress best as JPG via `sips`. Use JPG.
- Flat photographic shots that compress well as WebP (the existing gallery `webp2/` set) stay WebP — they're smaller than the JPG sips can produce.
- `sips` on this Mac cannot write `.webp` (only read). If you need new WebPs, ask Cole to export from Squoosh.app, or use the existing webp2/ source files.

**Image specs:**
- Target under ~250 KB each. Initial page load (hero + first portfolio piece) must stay under 1 MB.
- Bike portfolio (photos): 4:5 portrait crop, ~1100–1200px long edge.
- Prints and posters: natural aspect ratio (no crop). ~1200px long edge.
- Gallery: square (1:1), ~1400–2000px.
- Always update the `alt` text in `index.html` to describe what's pictured.

**Generating optimized images with `sips` (the only tool available):**
```
# JPG resize: -Z is "max long edge", formatOptions is JPEG quality 0-100
sips -s format jpeg -s formatOptions 70 -Z 1200 input.png --out output.jpg

# PDF → high-res PNG (sips alone renders PDFs at 72dpi). Use qlmanage instead.
qlmanage -t -s 2400 -o /tmp input.pdf
# Then sips the resulting .pdf.png to a JPG.
```

**HTML pattern:**
- Bike portfolio + gallery (photos, can crop): `<figure class="slot ratio-portrait">` or `<figure class="slot">` (gallery is 1:1).
- Prints + posters (flat artwork, do not crop): `<figure class="art-frame">` — shows image at natural ratio on a shell background.
- No `<picture>` element needed when only one format is present. Plain `<img>` is fine.

## 5. Voice
- First person. Calm, specific, concrete.
- The work speaks; copy doesn't oversell.
- Never use: "passionate," "innovative," "elevate," "curated," "we believe," "solutions."
- Be concrete about what kinds of opportunities are welcome.

## 6. Tech
- Static HTML, vanilla CSS, tiny vanilla JS for the broken-image graceful fallback.
- No frameworks, no build step, no dependencies beyond Google Fonts.
- Hosting: Netlify or Cloudflare Pages, custom domain when ready.

## 7. Contact (single source of truth)
- **Cole Dudley**
- Phone: 530-902-7227
- Email: colewdudley@icloud.com

If these change, update both this file and `index.html`.

---

*Last updated: 2026-05-10.*
