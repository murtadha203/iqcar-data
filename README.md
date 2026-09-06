# iqcars.net Complete Listing Archive

A single self-contained page presenting the archive of every vehicle listing published on
iqcars.net since October 2020. `index.html` is the whole site: no build step, no
dependencies, no data files. Fonts come from Google Fonts; everything else is inline.

## Publishing it on GitHub Pages

In the repository: **Settings > Pages > Source: Deploy from a branch > `main` / `/ (root)`
> Save.**

It appears at `https://murtadha203.github.io/iqcar-data/` within a minute or two.

**A published page on the free tier is a public page.** GitHub Pages on a private
repository needs a paid plan, so if these figures should not be public, host the file
somewhere access-controlled instead or share it directly.

## Editing the figures

Every number is either written in the HTML or sits in the constants at the top of the
`<script>` block: `MONTHS`, `TICKS`, `PRICE`, `BRANDS`, `ORIGIN`, `PERDAY`, `YTOT`. The
charts redraw from those, so changing a value is enough; nothing is baked into the SVG.

To regenerate them from the dataset:

```bash
python ../dash_stats.py     # writes ../dash_stats.json
python ../refresh_site.py   # pushes those figures into index.html
```

`refresh_site.py` asserts that every replacement matches exactly once, so a figure that
has drifted out from under its surrounding text fails loudly rather than going out wrong.

## Notes

- Light and dark are both designed; the page follows the reader's system setting.
- The first screen is locked to the viewport on a laptop and releases below 1000px wide
  or 540px tall, where it becomes a normal scrolling layout.
- No analytics, no trackers, no external requests except the font stylesheet.
