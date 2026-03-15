# Newsmash

A single-file RSS news aggregator. No build step, no backend — drop `index.html` anywhere and it works.

## Features

- Fetches RSS/Atom feeds via a public CORS proxy
- Mixed-height tile grid with auto-scroll
- Floating search bar, dark/light theme
- Configurable sources, refresh interval, and article retention
- PWA — installable on desktop and mobile, works offline

---

## Deploy to GitHub Pages

1. Fork or push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`, pick `main`, folder `/ (root)`.
4. Click **Save**. GitHub will publish the site at `https://<username>.github.io/<repo>/`.

> The service worker uses `start_url: "/"` — if you're serving from a subdirectory (e.g. `/newsmash/`), update `start_url` in `manifest.json` to match.

---

## Custom Domain (DNS)

### Using an apex domain (e.g. `newsmash.io`)

1. In your DNS provider add these **A records** pointing to GitHub's servers:

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

2. Also add an **AAAA record** set for IPv6 (optional but recommended — see [GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)).

3. In **Settings → Pages → Custom domain**, enter your domain and click **Save**. GitHub creates a `CNAME` file in the repo root automatically.

4. Wait for DNS to propagate (~5 min to 1 hour), then enable **Enforce HTTPS**.

### Using a subdomain (e.g. `app.example.com`)

1. Add a **CNAME record**:

   ```
   app.example.com → <username>.github.io
   ```

2. Enter the subdomain in **Settings → Pages → Custom domain** and save.

3. Enable **Enforce HTTPS** once the certificate is provisioned.

---

## Local development

```bash
npx serve .
# or
python3 -m http.server 8080
```

Open `http://localhost:8080`. The service worker requires HTTP (not `file://`).

### Pre-commit hooks

```bash
npm install   # installs prettier, htmlhint, husky
```

Commits run Prettier and HTMLHint against `index.html` automatically.
