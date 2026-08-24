# Skye Data — Landing Page

Static single-page site for **skye-data.net**. Brand colours and fonts are taken directly from the app's `globals.css` (cyan `#22d3ee` accent on `#0a0e14`, Inter + JetBrains Mono).

## Files
- `index.html` — the landing page, self-contained (Google Fonts via CDN, no build step)
- `book.html` — Cal.com booking embed
- `contact.html` — contact form → n8n webhook `skye-contact` → Supabase CRM `fdr_leads` + Gmail notify/auto-reply
- `calculator.html` — readout-burden cost calculator (vanilla JS, no build). Form posts to n8n webhook
  `skye-calculator` → inserts into `fdr_calculator_submissions` (Supabase "Skye Data Licensing" project,
  anon key + insert-only RLS) → Gmail notify to admin@ + auto-reply. Workflow: "Skye Data Calculator Leads" on n8n.
- `favicon.ico`

## Deploy via Netlify (recommended — already in your stack)
1. `git init && git add -A && git commit -m "Skye Data landing"` then push to a GitHub repo (e.g. `skye-data-landing`).
2. Netlify → **Add new site → Import from GitHub** → pick the repo. Build command: *none*. Publish directory: `.` (root).
3. Netlify → **Domain management → Add custom domain** → `skye-data.net` (add `www` too).
4. Add DNS records where `skye-data.net`'s DNS is managed (your registrar):
   - apex `@` → **A** `75.2.60.5` (or an ALIAS/ANAME to `<your-site>.netlify.app`)
   - `www` → **CNAME** `<your-site>.netlify.app`
   - **Do NOT remove the Google MX records**, or `jacques.binneman@skye-data.net` email breaks. Only add the web records alongside them.
5. Netlify auto-provisions HTTPS once DNS resolves.

## Alternative: GitHub Pages
- Repo → **Settings → Pages** → deploy from branch, root. Add custom domain `skye-data.net`.
- DNS: apex **A** records `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`; `www` **CNAME** → `<user>.github.io`. Keep MX intact.

## Xero
Set the Xero app's **Company or application URL** to `https://skye-data.net` once live.

## Editing notes
- Copy is value-led by design: no Skye pricing and no "cheaper than" claims anywhere on the site.
  The calculator shows only the visitor's own costs — keep it that way.
- Calculator seed figures (R8,000/outsourced readout, 0.6 h daily readout, 70 kg fuel waste) are
  editable defaults, not research-backed constants — Muller owns whether they change.
- All colours are CSS variables: `:root` in `styles.css` (site) and `.sheet` in `calculator.html` (worksheet).
