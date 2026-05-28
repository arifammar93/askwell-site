# AskWell Marketing Website

Static marketing site for AskWell, hosted on GitHub Pages at **askwell.tambourineai.com**.

## Files

- `index.html` — Long-scroll home page (hero, features, how it works, templates, pricing, roadmap, FAQ, CTA, footer)
- `privacy.html` — Privacy policy
- `logo.png` — Brand logo (used in nav, hero, footer, favicon, social card)
- `CNAME` — Tells GitHub Pages to serve this site at `askwell.tambourineai.com`
- `robots.txt` — Search engine directives
- `sitemap.xml` — Sitemap for search indexing

No build step. Pure HTML + CSS + a tiny bit of JS. Fonts pull from Google Fonts. Drop the files on any static host and it works.

## Deploy to GitHub Pages

1. Create a new GitHub repo (e.g. `askwell-site`) and push these files to the `main` branch.
2. In the repo: **Settings → Pages**.
3. Under "Build and deployment", set **Source** to `Deploy from a branch` and **Branch** to `main` / `(root)`.
4. Under "Custom domain", enter `askwell.tambourineai.com` and save. (The `CNAME` file already includes this.)
5. Check **Enforce HTTPS** once the cert provisions (can take a few minutes after DNS resolves).

## GoDaddy DNS setup

Since the apex domain `tambourineai.com` is on GoDaddy and you're using the `askwell` subdomain, add a **CNAME record** in GoDaddy:

| Type  | Name      | Value                          | TTL    |
|-------|-----------|--------------------------------|--------|
| CNAME | `askwell` | `<your-github-username>.github.io` | 1 hour |

Steps:

1. Log into GoDaddy → **My Products** → find `tambourineai.com` → **DNS**.
2. Click **Add New Record**.
3. Set **Type** to `CNAME`.
4. **Name**: `askwell` (just the subdomain part — not the full `askwell.tambourineai.com`).
5. **Value**: `<your-github-username>.github.io` (replace with your actual GitHub username; do **not** include `https://` or a trailing slash).
6. **TTL**: 1 hour is fine.
7. Save. DNS usually propagates in 5–60 minutes.

Once DNS resolves, GitHub Pages will automatically issue a TLS cert for the custom domain. Until then, the GitHub Pages settings page may show a warning — that's expected.

### Verifying DNS

```bash
dig askwell.tambourineai.com +short
# Should return: <your-github-username>.github.io
#                followed by the GitHub Pages IPs (185.199.108.153, etc.)
```

## Editing copy

All copy lives in `index.html` and `privacy.html`. Easy to find with Ctrl+F. The brand palette is defined as CSS variables at the top of each file:

```css
--cream:  #f4eedc;
--yellow: #f5c842;
--black:  #1a1a1a;
```

## Notes

- The "Install on Shopify" links currently point to `https://apps.shopify.com/` (placeholder). Replace with the actual app listing URL once published.
- The contact email is `support@tambourineai.com`. Swap it for a support@ alias whenever you set one up.
- Social/OG image is `logo.png`. Consider a wider 1200×630 OG card later for nicer Twitter/LinkedIn previews.
