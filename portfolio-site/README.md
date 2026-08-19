# Pedram Mozaffari — Interactive Portfolio

One page, eight tabs, eight design systems. Static site — no build step, no server code, no external CDNs. Everything (React, fonts, images) is self-hosted in `assets/`.

## Deploy

Any static host works. The folder containing this README is the site root.

- **Netlify** — drag this folder onto https://app.netlify.com/drop
- **Vercel** — `vercel` in this folder, or import the repo; framework preset: *Other*, no build command, output dir `.`
- **GitHub Pages** — push the contents to a repo, enable Pages on the branch root
- **Cloudflare Pages** — direct upload of this folder

Local preview: `python3 -m http.server` in this folder, then open http://localhost:8000 (double-clicking `index.html` also works in most browsers).

## After deploying

Set the social-preview image to an absolute URL in `index.html`:

```html
<meta property="og:image" content="https://YOUR-DOMAIN/assets/og.png">
```

## Swapping in real photos later

Product and scene images are the SVG illustrations in `assets/img/`. To replace one with a photo, either:

1. keep the filename and format (overwrite e.g. `assets/img/lea-hero.svg`), or
2. drop in a `.jpg`/`.webp` and update the matching `src="assets/img/…"` attribute on the `<image-slot>` in `index.html`. Product cards use the templated `src="assets/img/{{ p.slotId }}.svg"` — slot ids are `volta-circuit`, `volta-static`, `volta-ampere`, `volta-ohm`, `volta-flux`, `volta-pulse`.

Images render with `object-fit: cover`, so any reasonable aspect ratio crops cleanly.

## Where things live

- `index.html` — all markup (per-tab sections) plus the page logic in the `<script type="text/x-dc">` block at the bottom: products, prices, FAQ, dashboard rows, reservation state. Edit copy and data there.
- `assets/js/` — React 18.3.1 UMD, the design-component runtime, and the `<image-slot>` element.
- `assets/fonts/` — self-hosted WOFF2 subsets (browsers download only the subsets a page actually uses).
- `assets/img/` — the 13 SVG illustrations (VOLTA sneakers, Verdi leaf, Trattoria Nonna Lea scenes).
