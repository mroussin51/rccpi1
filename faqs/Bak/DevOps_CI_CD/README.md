# RCCPI FAQS Integration Bundle

This bundle adds Answer‑Engine‑Optimized (FAQS) pages to **rccpi.net** without changing your site’s look & feel.

## What’s included
- `/faqs/` — 14 HTML outline pages (answer‑first with JSON‑LD embedded) + an index
- `robots.txt` — references the sitemap
- `sitemap.xml` — lists `/faqs/` pages
- Install script and copy‑paste commands

## Quick install (static site on Linux)
> Assumes your web root is `~/docker/rccpi.net/site`

```bash
# 1) Backup
rsync -a --delete ~/docker/rccpi.net/site/ ~/docker/rccpi.net/site_backup_$(date +%F)/

# 2) Unzip into the site root
cd ~/docker/rccpi.net/site
unzip ~/Downloads/rccpi_faqs_integration_bundle.zip

# 3) If you already have robots.txt or sitemap.xml, merge manually (see below).
#    Otherwise, the provided files are safe defaults.

# 4) (Optional) If serving via Docker, restart the web container
docker compose ps || true
docker compose restart || true
```

### Merge notes
- **robots.txt**: Keep your existing allows/disallows and add:
  ```
  Sitemap: https://rccpi.net/sitemap.xml
  ```
- **sitemap.xml**: If you have one already, copy the `<url>` entries from this bundle into it.

### Add a nav link to the new guides
Insert this HTML into your header/nav where you want the link:
```html
<li><a href="/faqs/">Guides &amp; How‑tos</a></li>
```

### Nginx tips (optional)
Ensure HTML is served with caching that allows quick updates for HTML (e.g., `Cache-Control: no-cache`) and longer cache for CSS/JS/images. ACME/SSL remains unchanged.

---

**Author**: Rosario Roussin · **Last updated**: 2025-09-28
