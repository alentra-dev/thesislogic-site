# thesislogic.com — promotional site

Static site for [ThesisLogic](https://github.com/alentra-dev/thesislogic), served by GitHub Pages
at **https://thesislogic.com**. No build step, no dependencies — edit `index.html`, push, done.

## Launch checklist (one-time)

### 1. DNS (at your registrar for thesislogic.com)

| Type  | Host | Value |
|-------|------|-------|
| A     | @    | 185.199.108.153 |
| A     | @    | 185.199.109.153 |
| A     | @    | 185.199.110.153 |
| A     | @    | 185.199.111.153 |
| CNAME | www  | alentra-dev.github.io |

Then in this repo's **Settings → Pages**, confirm the custom domain shows `thesislogic.com` and
tick **Enforce HTTPS** once the certificate is issued (can take up to an hour after DNS
propagates). Optionally park `thesislogic.ai` with a redirect to thesislogic.com at the
registrar level.

### 2. Contact form (Formspree — free tier)

1. Create a free account at [formspree.io](https://formspree.io) using **info@thesislogic.com**.
2. Create a form; copy its endpoint (`https://formspree.io/f/xxxxxxx`).
3. In `index.html`, replace `YOUR_FORM_ID` in the form's `action` with the real ID.

Until you do this, the form gracefully falls back to composing an email to info@thesislogic.com
in the visitor's mail client, so contact works from day one. The form includes a honeypot field
for spam bots, and the email address is never present in the static HTML (assembled on click,
so scrapers don't harvest it).

### 3. Analytics (GoatCounter — free, cookieless, GDPR-friendly)

1. Register at [goatcounter.com](https://www.goatcounter.com) with the code **thesislogic**
   (so your dashboard is `https://thesislogic.goatcounter.com`).
2. Nothing else — the snippet at the bottom of `index.html` already points there.

GoatCounter gives you referrers, pages, countries, browsers, and campaign parameters without
cookies or personal data — no consent banner needed, consistent with the responsible-AI brand.
Track campaigns with `?utm_campaign=...` URLs (e.g. in conference bios or LinkedIn posts).

### 4. Search engines

- `sitemap.xml` and `robots.txt` are included; submit https://thesislogic.com/sitemap.xml in
  [Google Search Console](https://search.google.com/search-console) (verify the domain via a DNS
  TXT record) and Bing Webmaster Tools.
- Structured data (JSON-LD: SoftwareApplication + Person + WebSite) is embedded in `index.html`;
  validate at https://search.google.com/test/rich-results after launch.

## Editing notes

- Single-file site: all CSS/JS inline in `index.html`; dark mode follows the OS preference.
- The hero animation ("proof-gate demo") is a scripted timeline in the `runDemo()` function.
- `og-card.png` is the social-share image (1200×630); regenerate if branding changes.
- Keep the footer disclaimer line — it mirrors the project's DISCLAIMER.md.
