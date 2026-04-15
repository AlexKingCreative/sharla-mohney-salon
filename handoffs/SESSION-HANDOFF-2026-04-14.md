# Session Handoff - 2026-04-14

**Repo:** `/Users/kingy/sharla-mohney-salon` (separate from company-os-1)
**Branch:** `main`
**GitHub:** https://github.com/AlexKingCreative/sharla-mohney-salon
**Preview URL:** https://sharla-mohney-salon.vercel.app
**Target domain:** sharlamohneysalon.com (DNS NOT yet switched)
**Session focus:** Full WordPress -> static HTML rebuild for Sharla Mohney Salon via site-launch skill.

## Completed This Session

- Built 4 static HTML pages:
  - `/Users/kingy/sharla-mohney-salon/index.html` - nav, hero (slider-bg51.jpg bg), 3 service cards, credentials bar, about, 6 testimonials, CTA, contact (hours + Vagaro booking card), footer. `HairSalon` JSON-LD schema.
  - `/Users/kingy/sharla-mohney-salon/services.html` - full services detail (extensions/hair/color/makeup/photo-shoots), 31-item filterable portfolio gallery (vanilla JS), `FAQPage` schema.
  - `/Users/kingy/sharla-mohney-salon/brand.html` - brand guide (unlinked, `noindex`).
  - `/Users/kingy/sharla-mohney-salon/404.html` - custom error page.
- Infra files: `vercel.json`, `robots.txt`, `sitemap.xml`, `_original-copy.md` (preserved original source copy).
- Typography: Montserrat (headings) + Mulish (body), per her originals.
- Meta descriptions trimmed to <160 chars; copyright year set to 2026.
- **Brand color locked after 3 iterations:**
  1. My warm gold `#C9A96E` - rejected.
  2. Blue `#4C86E5` from original WP theme CSS - rejected.
  3. Hot pink `#F52D8C` (pixel-sampled directly from logo PNG), `accent-dark: #C42470` - ACCEPTED. All 4 HTML files updated.
- Final commit `647ba12` "feat: update brand accent color to hot pink #F52D8C" pushed to `origin/main`. Vercel auto-redeploying.

## In Progress (Not Finished)

- **Vercel redeploy** for commit `647ba12` triggered at session end. Next session should verify preview looks correct with pink branding before doing anything else.

## Blockers

- **Image references still point to original domain.** The site currently references assets (hero bg `slider-bg51.jpg`, service icons, portfolio photos) via the live `sharlamohneysalon.com` URLs. If DNS switches before these are downloaded and committed locally, the site will break. This is the #1 blocker to going live.
- **Client approval gate.** Sharla must review + approve preview URL before any DNS work or analytics/GSC setup.

## Decisions Made

- Brand accent color is `#F52D8C` (hot pink from logo), `#C42470` dark variant. Do not change without Sharla's explicit approval - this was the third iteration.
- Keep `brand.html` unlinked and `noindex`. It's an internal reference, not a public page.
- Static HTML + Vercel (not a framework). Site-launch skill workflow.
- Preserve original copy verbatim in `_original-copy.md` for future reference / re-edits.

## System State

- **Uncommitted changes (sharla-mohney-salon):** none - working tree clean.
- **Recent commits (sharla-mohney-salon):**
  - `647ba12` feat: update brand accent color to hot pink #F52D8C
  - `e2c731a` Rebrand to original colors: blue #4C86E5 + Montserrat/Mulish fonts, use slider hero images and service icons
  - `03a1aa4` Initial build: Sharla Mohney Salon website rebuild
- **Files in repo root:** `404.html`, `_original-copy.md`, `brand.html`, `index.html`, `robots.txt`, `services.html`, `sitemap.xml`, `vercel.json`. No `images/` or `favicon.ico` yet.
- **Company-os-1:** not touched this session. State unchanged from prior `SESSION-HANDOFF-2026-04-14-2030.md`.

## Next Session Should

1. **Visually verify preview** at https://sharla-mohney-salon.vercel.app - confirm pink `#F52D8C` is live on all pages and layout is intact.
2. **Download every image referenced on the live site** (hero slider backgrounds, service icons, 31 portfolio photos, any logos) into `/Users/kingy/sharla-mohney-salon/images/` and rewrite `<img>` / CSS `background-image` URLs to relative paths (`/images/...`). Commit.
3. **Generate favicon:** `magick /Users/kingy/sharla-mohney-salon/logo.png -resize 32x32 /Users/kingy/sharla-mohney-salon/favicon.ico` (requires logo.png to be placed in repo first) and add `<link rel="icon">` to all pages.
4. **Send preview URL to Sharla for approval.** Do not proceed past this step without her go-ahead.
5. **Phase 6 (post-approval):** DNS cutover to `sharlamohneysalon.com` - Vercel A record `76.76.21.21`. Add domain in Vercel project settings.
6. **Phase 7:** Google Search Console verification + submit `sitemap.xml`.
7. **Phase 8:** Analytics (GA4 or Cloudflare Web Analytics).

## Memory Suggestions

- **Salon rebuild image-local rule:** For any WordPress -> static rebuild, download all referenced images into the new repo BEFORE DNS cutover. References to the old domain silently break at cutover. Worth adding to the `site-launch` skill if not already there.
- **Color sampling lesson:** When a client has a logo but no documented brand palette, pixel-sample the logo PNG directly. Don't infer colors from the old site's CSS theme file (could be a template default, not her choice) and don't invent from "vibes" (warm gold was a miss). Worth noting in site-launch skill.
- **Sharla Mohney Salon project metadata** (repo path, preview URL, target domain, accent colors) is worth a short memory entry under `01-System-Config/` so future sessions can pick up without this handoff.
