# Botly — WhatsApp customer-support chatbot landing page

Hebrew (RTL) marketing landing page for **Botly**, a customer-support WhatsApp bot for the Israeli market.

**Live:** https://bot-ly.site (and https://www.bot-ly.site)

## Structure

| Path | What |
|------|------|
| `public/` | The deployed website (this is the web root) |
| `public/index.html` | Single-page landing (self-contained: inline CSS/JS, fonts + GSAP from CDN) |
| `public/terms.html`, `public/privacy.html`, `public/accessibility.html` | Legal pages |
| `public/logo.png`, `public/example.png` | The only images the page uses |

Only the contents of `public/` are uploaded to Cloudflare. Ad creatives and other
binaries are kept out of the repo (git-ignored), not version-controlled here.

## Deployment

Hosted on **Cloudflare Pages** (project `replai-landing`). Every push to `main` that
touches `public/**` automatically deploys to **production** via GitHub Actions
(`.github/workflows/deploy.yml`), which runs:

```
wrangler pages deploy public --project-name=replai-landing --branch=main
```

You can also trigger a deploy manually from the **Actions** tab ("Run workflow").

### Required GitHub secrets

- `CLOUDFLARE_API_TOKEN` — Cloudflare API token with **Account → Cloudflare Pages → Edit**.
- `CLOUDFLARE_ACCOUNT_ID` — the Cloudflare account ID.

No credentials or IDs are stored in the repository — both come from GitHub Actions secrets.

### Editing the site

Edit files in `public/`, commit, and push to `main` — the deploy runs automatically.
To preview locally, just open `public/index.html` in a browser.
