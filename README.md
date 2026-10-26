# SEVENPLUS Recovery Jewelry — Shopify LP

Image-stack landing page for the SEVENPLUS "Recovery Jewelry" (リカバリージュエリー)
product, built to paste directly into a Shopify product description / page editor.

## Files

- `shopify-snippet.html` — the paste-ready HTML fragment. This is the only file
  whose contents go into Shopify.
- `index.html` — local preview wrapper (loads the same markup from `assets/`
  via relative paths) so the layout can be checked in a browser before
  touching Shopify. Not for upload.
- `assets/lp-01.jpg` … `lp-08.jpg` — the 8 main source images in display
  order, resized to a consistent 750px width and re-compressed as JPEG q85.
- `assets/lp-09.png` — closing tagline section ("身につけるだけで、心も身体も、
  心地よく。"), placed as the final content section before the last CTA.
  Kept as PNG (alpha channel).
- `assets/cta-button.png` — the repeated CTA button ("商品はこちら"), cropped
  tight to its visible content and resized to 660px wide, alpha preserved
  (kept as PNG, not converted to JPEG).

## How to publish on Shopify

1. In Shopify Admin, go to **Content → Files** and upload all 10 files from
   `assets/` (the 9 `lp-01.jpg` … `lp-08.jpg` / `lp-09.png` images plus
   `cta-button.png`; keep these filenames so they're easy to match back to
   the snippet).
2. For each uploaded file, copy its CDN URL (click the file → "Copy link",
   something like `https://cdn.shopify.com/s/files/1/XXXX/XXXX/files/lp-01.jpg`).
3. Open `shopify-snippet.html`, and for each `<img src="lp-XX.jpg">` /
   `<img src="cta-button.png">`, replace the filename with the matching CDN
   URL.
4. Replace every `href="#buy"` on the 5 CTA button links with the actual
   purchase destination — either the product's own URL/variant link, or an
   in-page anchor that scrolls back up to this product's Add to Cart button
   (the exact anchor ID depends on the theme; check with the theme's HTML
   if unsure).
5. Open the target product (or page) in Shopify Admin, switch the
   description editor to **"Show HTML"** (`< >` icon in the rich text
   toolbar), and paste the edited contents of `shopify-snippet.html` in.
6. Save, then preview the product/page on both desktop and mobile — the
   images are set to `width:100%` with no fixed container, so they will
   scale to whatever width Shopify's theme gives the description area.

## Notes

- Image order follows the numbering in the original export (01 → 08), with
  `lp-09.png` appended as the closing section.
- The first image uses `loading="eager" fetchpriority="high"` (likely LCP
  element); the rest are `loading="lazy"`.
- `width`/`height` attributes are set to each image's native pixel size to
  reserve layout space and avoid cumulative layout shift.
- All styling is inline (no `<style>` block) so the markup survives editors
  that strip `<style>` tags from pasted HTML.
- The CTA button repeats 5 times, placed at each natural decision point:
  after 01 (hero), after 03 (pain-point agitation), after 05 (materials/
  mechanism), after 07 (EMC-sheet feature), and after 08 (testimonials/
  social proof — placed immediately after, while trust is highest). It is
  deliberately NOT placed after 04 or 06 — those are curiosity-hook
  transition banners that lead into 05/07, and a CTA there would break the
  hook before its payoff. There is also no CTA after 09 (closing tagline) —
  09 immediately follows the 08 CTA, so one final button there was
  redundant. All 5 currently point to `href="#buy"`, a placeholder — see
  step 4 above.
