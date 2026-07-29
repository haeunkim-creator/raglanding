Lucy marketing site — deliverable
=================================

Open "Lucy Marketing Site.dc.html" in a browser. Keep the folder intact:
the page loads support.js, image-slot.js, and assets/ by relative path.

  Lucy Marketing Site.dc.html   the page
  support.js / image-slot.js    runtime (do not edit)
  assets/hero.mp4               hero video (autoplay, muted, loop)
  assets/hero-3panel.png        video poster frame
  assets/chunk-highlight.png    supplied screenshot (portrait 2:3)
  DESIGN_HANDOFF.md             implementation spec, 19 sections
  COPY_DECK.md                  full English copy + Korean gloss

Fonts load from a CDN; without a connection the page falls back to system faces.

Four image frames are still placeholders and show their target filename:
  pipeline-detail.png      Proof, column 01   4:3
  chunk-highlight.png      Proof, column 02   4:3  (current file is 2:3 - needs a 4:3 crop)
  judge-metrics.png        Proof, column 03   4:3
  table-before-after.png   Why it works       16:9, 2000px+ wide

Three figures render as [TO CONFIRM] on the page and must be resolved before launch:
API endpoint shape and auth model, delivery methods, and the licensing terms line.
