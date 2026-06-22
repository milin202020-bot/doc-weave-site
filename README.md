# doc-weave.co.in — marketing site

Static site for DocWeave. Plain HTML, no build step, no dependencies.

```
index.html          → https://doc-weave.co.in/
pricing/index.html  → https://doc-weave.co.in/pricing   (the in-app Upgrade button opens this)
CNAME               → custom-domain file GitHub Pages reads (contains doc-weave.co.in)
```

## Deploy via GitHub Pages (free)

1. **Create a new public repo** on GitHub, e.g. `doc-weave-site`.
2. **Push these files** to it:
   ```bash
   cd "doc-weave-site"
   git init
   git add .
   git commit -m "DocWeave marketing site: landing + pricing"
   git branch -M main
   git remote add origin https://github.com/<your-user>/doc-weave-site.git
   git push -u origin main
   ```
3. **Enable Pages:** repo → Settings → Pages → Source = `Deploy from a branch`, Branch = `main` / `/ (root)` → Save.
4. **Custom domain:** still on the Pages screen, set Custom domain = `doc-weave.co.in` (the CNAME file already declares it). Tick **Enforce HTTPS** once it's available.

## DNS at GoDaddy (domain stays registered with GoDaddy)

In GoDaddy → your domain → DNS, add:

| Type  | Name | Value                | Notes |
|-------|------|----------------------|-------|
| A     | @    | 185.199.108.153      | GitHub Pages |
| A     | @    | 185.199.109.153      | GitHub Pages |
| A     | @    | 185.199.110.153      | GitHub Pages |
| A     | @    | 185.199.111.153      | GitHub Pages |
| CNAME | www  | <your-user>.github.io | www → Pages |

Delete any conflicting GoDaddy "Parked"/forwarding A-records on `@` first.
DNS can take 15 min–2 h to propagate. Then `https://doc-weave.co.in/pricing` is live.

## Editing

- **Prices:** open `pricing/index.html`, search for `EDIT PRICE`. Change currency/numbers only.
- **Download button:** `index.html`, search for `EDIT` — point it at your public GitHub release once the app repo/release is public (currently a mailto).
- **Buy buttons:** currently `mailto:support@doc-weave.co.in`. Swap for Gumroad / Lemon Squeezy checkout links when your store is live.
