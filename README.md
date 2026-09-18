# eLumino website

Static site — open `index.html`, or deploy the folder as-is (Vercel/Netlify/any static host).

- `index.html` — company page
- `apps/*.html` — one landing page per app (Prenatal Compass, Loonlight, TenKicks, GiggleGuardian)
- `assets/site.css` — shared styles; each app re-themes via `[data-app="…"]` using that app's own palette + fonts
- `assets/shots/` — screenshots (JPG, iPhone aspect 1206×2622); `assets/icons/` — app icons

## Adding real download links
On each `apps/<app>.html`, the "Coming soon to App Store / Google Play" buttons are
`<span class="dl soon">…</span>` (they appear twice per page: hero + "Get" band). Replace one with:

```html
<a class="dl live" href="https://apps.apple.com/…" target="_blank" rel="noopener">
  <span class="ms">phone_iphone</span><span><small>Download on the</small><strong>App Store</strong></span>
</a>
```
(use `android` as the icon name for Google Play). Also flip the "Coming soon" badge on that app's card in `index.html`
(`<span class="ac-status">` → add class `live`, change the text).

## Replacing screenshots
Drop a new JPG at the same filename in `assets/shots/`. Web/design captures without an iOS status bar use the
`inset` class on `.phone-screen` so the Dynamic Island sits in clear space.

## Deploying to GitHub Pages
All links and asset paths are relative, so the site works at `https://<user>.github.io/<repo>/` as well as on a custom domain.
1. Put the contents of this folder at the root of a repo (e.g. `elumino-website`) and push to `main`.
2. Repo → Settings → Pages → Source: *Deploy from a branch* → `main` / `(root)`.
3. For `elumino.ca`: add a `CNAME` file containing `elumino.ca`, set the custom domain in Pages settings, and point the domain's DNS at GitHub Pages.
