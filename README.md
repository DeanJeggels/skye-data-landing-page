# Skye Data — Landing Page

Static single-page site for **skye-data.net**. Brand colours and fonts are taken directly from the app's `globals.css` (cyan `#22d3ee` accent on `#0a0e14`, Inter + JetBrains Mono).

## Files
- `index.html` — the page, self-contained (Google Fonts via CDN, no build step)
- `favicon.ico`

## Deploy via Netlify (recommended — already in your stack)
1. `git init && git add -A && git commit -m "Skye Data landing"` then push to a GitHub repo (e.g. `skye-data-landing`).
2. Netlify → **Add new site → Import from GitHub** → pick the repo. Build command: *none*. Publish directory: `.` (root).
3. Netlify → **Domain management → Add custom domain** → `skye-data.net` (add `www` too).
4. Add DNS records where `skye-data.net`'s DNS is managed (your registrar):
   - apex `@` → **A** `75.2.60.5` (or an ALIAS/ANAME to `<your-site>.netlify.app`)
   - `www` → **CNAME** `<your-site>.netlify.app`
   - **Do NOT remove the Google MX records**, or `admin@skye-data.net` email breaks. Only add the web records alongside them.
5. Netlify auto-provisions HTTPS once DNS resolves.

## Alternative: GitHub Pages
- Repo → **Settings → Pages** → deploy from branch, root. Add custom domain `skye-data.net`.
- DNS: apex **A** records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; `www` **CNAME** → `<user>.github.io`. Keep MX intact.

## Xero
Set the Xero app's **Company or application URL** to `https://skye-data.net` once live.

## Editing notes
- Pricing in the "barrier" section is intentionally soft ("a fraction of that"). Put exact figures back in by editing the `.bar-fill.skye` width and the `.price` label if you want hard numbers.
- All colours are CSS variables in the `:root` block at the top of `index.html`.
