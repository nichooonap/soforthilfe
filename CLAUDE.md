# Soforthilfe

Mother brand (`onlinesoforthilfe.de`) for quick-help tools targeting local businesses. Each subdomain is a standalone product.

## Concept
Joé uses these for lead generation — finds businesses missing something online and pitches them a fix.

## Structure (per product)
- `website/` — landing page HTML
- `print/` — flyers, PDFs
- `ads/` — Instagram posts, digital formats

## Legal pages

All legal documents live on the main domain at:
- `onlinesoforthilfe.de/impressum.html`
- `onlinesoforthilfe.de/datenschutz.html`
- `onlinesoforthilfe.de/agb.html`
- `onlinesoforthilfe.de/widerruf.html`

The `legal/` folder contains the source HTML + PDF versions (local only, not deployed).

### Sync rule — MUST follow when updating legal documents:
1. Update the HTML in `legal/agb.html`, `legal/datenschutz.html`, `legal/widerruf.html`
2. Regenerate the PDFs (`legal/agb.pdf`, `legal/datenschutz.pdf`, `legal/widerruf.pdf`) via `python3 legal/generate_pdfs.py`
3. Copy the updated content into the root HTML pages (`agb.html`, `datenschutz.html`, `widerruf.html`, `impressum.html`)
4. Commit and push → triggers auto-deploy of main `onlinesoforthilfe.de`
5. Run `vercel deploy <dir> --prod --yes` for each subproject: `geo/ googleads/ keywords/ maps/ seo/ website/`

All subproject footers already link to `onlinesoforthilfe.de` legal pages — no changes needed there unless a new subproject is added. When adding a new subproject, copy the footer pattern from any existing subproject.

