# Private Logic website

A simple, static, single-page site for Private Logic LLC. No build step, no
dependencies, no trackers: plain HTML and CSS in `public/`, with automatic
light and dark themes.

```
public/
  index.html    # the site
  styles.css    # all styling
  favicon.svg   # logo / favicon
  404.html      # served by Cloudflare for unknown paths
  _headers      # security + cache headers (Cloudflare Pages)
  robots.txt
```

## Preview locally

```sh
cd public && python3 -m http.server 8000
# open http://localhost:8000
```

## Host for free on Cloudflare Pages

### Option A: connect this GitHub repo (auto-deploys on every push)

1. Log in to the Cloudflare dashboard and go to **Workers & Pages → Create → Pages → Connect to Git**.
2. Pick the `privatelogic/plsite` repository.
3. Build settings:
   - **Framework preset:** None
   - **Build command:** *(leave empty)*
   - **Build output directory:** `public`
4. Click **Save and Deploy**. The site goes live at `https://<project>.pages.dev`.

Every push to the production branch (e.g. `main`) redeploys automatically, and
other branches get their own preview URLs.

### Option B: upload directly from your machine

```sh
npx wrangler pages deploy public --project-name=privatelogic
```

### Custom domain

In your Pages project open **Custom domains → Set up a custom domain** and
enter your domain (e.g. `privatelogic.com`). If the domain's DNS is already on
Cloudflare this is a single click; otherwise follow the prompts to add the DNS
record. HTTPS is provisioned automatically.

## Editing

- **Contact email:** search `index.html` for `hello@privatelogic.com` and replace both occurrences.
- **Copy:** all text lives in `index.html`.
- **Colors:** change `--accent` / `--accent-2` at the top of `styles.css` (light and dark values).
