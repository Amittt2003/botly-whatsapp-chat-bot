# Botly — WhatsApp customer-support chatbot landing page

Hebrew (RTL) marketing landing page for **Botly**, a customer-support WhatsApp bot for the Israeli market.

**Live:** https://bot-ly.site (and https://www.bot-ly.site)

## Structure

| Path | What |
|------|------|
| `public/` | The deployed website (this is the web root) |
| `public/index.html` | Single-page landing (self-contained: inline CSS/JS, fonts + GSAP from CDN) |
| `public/terms.html`, `public/privacy.html`, `public/accessibility.html` | Legal pages |
| `public/logo.png`, `public/example.png` | Images used by the site |
| `ads/` | Meta ad creatives (not deployed) |
| `shark-logo.png` | Unused legacy mascot, kept for history (not deployed) |

Only the contents of `public/` are uploaded to Cloudflare.

## Deployment

Hosted on **Cloudflare Pages** (project `replai-landing`). Every push to `main` that
touches `public/**` automatically deploys to **production** via GitHub Actions
(`.github/workflows/deploy.yml`), which runs:

```
wrangler pages deploy public --project-name=replai-landing --branch=main
```

You can also trigger a deploy manually from the **Actions** tab ("Run workflow").

### Required GitHub secret

- `CLOUDFLARE_API_TOKEN` — Cloudflare API token with **Account → Cloudflare Pages → Edit**.

The Cloudflare account ID is set directly in the workflow.

### Editing the site

Edit files in `public/`, commit, and push to `main` — the deploy runs automatically.
To preview locally, just open `public/index.html` in a browser.
