# Lucy marketing site — Vercel deploy

The 404 was a routing problem, not a build problem: the page was named
`Lucy Marketing Site.dc.html`, and Vercel only serves a directory root when it
finds `index.html`. This folder is the same page renamed and flattened for
static hosting.

## Deploy

Push the **contents of this folder** to the repository root:

    index.html
    support.js
    image-slot.js
    assets/hero.mp4
    assets/hero-3panel.png
    assets/chunk-highlight.png
    assets/pipeline-detail.png
    assets/judge-metrics.png
    assets/table-before-after.png

Then in Vercel: **Framework Preset → Other**, leave Build Command empty, and set
Output Directory to the repo root (or leave it empty). No build step is needed —
these are static files.

If you keep the files in a subfolder inside the repo, set Vercel's **Root
Directory** to that folder instead of moving anything.

## Do not rename

`index.html` loads `./support.js`, `./image-slot.js`, and `./assets/*` by
relative path. Keep the filenames and the `assets/` folder name as they are.

## Notes

- Fonts load from Google Fonts and jsDelivr CDNs, so the deployed page needs a
  network connection to render Archivo and Pretendard. Without it, system faces
  substitute.
- `assets/hero.mp4` is 17 MB. It is within Vercel's static file limits, but the
  first load on a slow connection will show the poster frame
  (`assets/hero-3panel.png`) until the video buffers. A 720p re-encode would cut
  this substantially.
- All four screenshot frames are filled and no `[TO CONFIRM]` markers remain.
- Not on the page, for lack of source data: dataset scale figures, licensing and
  redistribution terms, security/compliance statements, a competitive benchmark,
  and customer references. Each needs a real number or policy before it can ship.
