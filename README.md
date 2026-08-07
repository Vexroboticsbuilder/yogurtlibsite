# 210E Toolkit — yogurtlib.com

Plain HTML/CSS/JS site, no build step. Replaces the old Google Sites page.

## Structure
```
index.html                      homepage / hub
assets/style.css                shared design tokens, nav, footer
tools/custom-pather/index.html  the pathing tool
tools/data-visualizer/index.html placeholder for the second tool
docs/                           documentation pages
CNAME                           custom domain for GitHub Pages (yogurtlib.com)
```

## Deploy with GitHub Pages (recommended)

1. Create a new GitHub repo (e.g. `210e-toolkit`) and push this folder's contents to the `main` branch:
   ```bash
   cd yogurtlib-site
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/210e-toolkit.git
   git push -u origin main
   ```
2. In the repo on GitHub: **Settings → Pages**. Under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
3. GitHub will give you a URL like `https://<your-username>.github.io/210e-toolkit`. Confirm the site loads there first.

## Point yogurtlib.com at it

1. Register `yogurtlib.com` with a registrar (Cloudflare Registrar or Namecheap both work well and support `.dev`).
2. In your DNS provider, add these records (GitHub Pages requires **A records for the apex domain**, not a CNAME, since CNAMEs aren't allowed on the root/apex):
   ```
   Type   Name   Value
   A      @      185.199.108.153
   A      @      185.199.109.153
   A      @      185.199.110.153
   A      @      185.199.111.153
   ```
   If you also want `www.yogurtlib.com` to work, add:
   ```
   CNAME  www    <your-username>.github.io
   ```
3. Back in **Settings → Pages** on GitHub, enter `yogurtlib.com` as the custom domain and save. This writes the same `CNAME` file already included in this repo. Check **Enforce HTTPS** once the option becomes available (may take a few minutes to a few hours after DNS propagates) so visitors always get the secure `https://` version.
4. DNS changes can take anywhere from a few minutes to 24 hours to propagate. You can check status with `dig yogurtlib.com`.

## Adding tools or docs later

See `docs/site-guide.html` on the live site, or open the file directly — it documents the folder pattern and how the nav/footer are wired across pages.

## Alternative: Netlify

If you'd rather not use GitHub Pages: drag this whole folder onto https://app.netlify.com/drop for an instant deploy, then in **Site settings → Domain management** add `yogurtlib.com` as a custom domain — Netlify will give you the DNS records to add (usually a single `A` record or Netlify's own nameservers, shown in their dashboard).
