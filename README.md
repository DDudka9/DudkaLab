# Dudka Lab Website

A static website (plain HTML + CSS, no frameworks) for the Dudka Lab at Lehigh University.

> **What's a placeholder?** All the schematics and the main paragraph on the home
> page are left blank for you to fill in. Replace them when you're ready — the
> site already works, so you can deploy first and customize as you go.

## Folder structure

```
dudka-lab-website/
├── index.html                     # Home page
├── CNAME                          # Custom domain (edit to match yours)
├── css/
│   └── style.css                  # Single stylesheet (CSS variables at top)
├── images/
│   ├── hero.png                   # Hero image (yours — restored)
│   ├── damian.jpg                 # PI headshot
│   ├── cellimage.png              # Small cell image
│   ├── cellhero.jpg               # Alternative cell image
│   ├── LabOverview.png            # Schematic on the home page
│   ├── lehighlogo.png             # Official Lehigh horizontal logo
│   ├── lehighseal.png             # Official Lehigh seal
│   └── schematics/                # SVG placeholders — replace with your own
│       ├── dir1-origin-of-evolution.svg
│       ├── dir2-adaptive-evolution.svg
│       ├── dir3-health-implications.svg
│       ├── pub-nature-2025.svg
│       ├── pub-cenpt-2025.svg
│       ├── pub-freeda-2023.svg
│       ├── pub-hurp-2019.svg
│       └── pub-merotelic-2018.svg
└── pages/
    ├── research.html              # Research directions (full)
    ├── publications.html          # Articles / Methods / Reviews
    ├── people.html                # Lab members
    └── join.html                  # Open positions
```

---

## What needs your input (placeholder list)

1. **Main paragraph on home page** — open `index.html`, search for
   `MAIN PARAGRAPH PLACEHOLDER`, replace the italic placeholder `<p>...</p>`
   with your own text.
2. **8 schematics** — every file in `images/schematics/` is currently a dashed
   "Schematic placeholder" rectangle. Replace each one with your own SVG using
   the same filename so the HTML doesn't need editing.
3. **Contact email** — search across the project for `dad526@lehigh.edu` and
   replace with your real Lehigh address.
4. **Lab members** — open `pages/people.html`, copy the commented-out
   `<div class="person-card">…</div>` block, uncomment it, and fill in details.

---

## 1 · Get a domain (~$10–15/year)

Three good registrars (any works):

| Registrar | Pros | URL |
|---|---|---|
| **Porkbun** | cheapest, free WHOIS privacy, no upsells | <https://porkbun.com> |
| **Namecheap** | popular, easy DNS panel | <https://www.namecheap.com> |
| **Cloudflare Registrar** | at-cost pricing | <https://www.cloudflare.com/products/registrar/> |

### A. Choosing a domain name

- `dudkalab.me`  ← **modern, short, memorable** (≈ $4 first year, ~$15/yr after)
- `dudkalab.com` ← classic and safe (~$10–13/yr)
- `dudkalab.org` (~$11/yr)
- `dudkalab.science` or `dudkalab.bio` (~$15–25/yr — longer but topical)

> **Tip:** `.me` is a country-code TLD (Montenegro) but is widely used for
> personal/lab sites. It's perfectly fine for academic websites. Avoid
> domains that look phishy (`dudka-lab.xyz`) — search engines de-rank these.

### B. Buying it

1. Go to your chosen registrar.
2. Search for the name you want.
3. Add to cart. **Decline every upsell** (hosting, email, "premium SSL", etc).
4. Pay. Most registrars include free WHOIS privacy.
5. Set auto-renew so you don't lose the domain in a year.

You now own the domain but it points nowhere yet. Next step: hosting.

---

## 2 · Host the site on GitHub Pages (free)

GitHub Pages is the standard for academic lab sites: free, fast, HTTPS by
default, and your repository doubles as backup + version history.

### A. Make a GitHub account (skip if you have one)

Go to <https://github.com> → Sign up.

### B. Create the repository

1. Click the **+** in the top-right → **New repository**.
2. Repository name: `dudka-lab-website` (any name works).
3. Set to **Public** (required for free GitHub Pages).
4. Do **not** initialize with a README (we already have one).
5. Click **Create repository**.

### C. Upload these files

#### Option 1 — Drag & drop in the browser (no command line)

1. On the new repo page, click **uploading an existing file**.
2. Drag the **contents** of this `dudka-lab-website` folder
   (i.e., `index.html`, `css/`, `images/`, `pages/`, `CNAME`, `README.md`)
   — **not** the wrapping folder itself.
3. Scroll down → "Commit changes" → green button.

#### Option 2 — Git command line

```bash
cd /path/to/dudka-lab-website
git init
git add -A
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/dudka-lab-website.git
git push -u origin main
```

### D. Turn on GitHub Pages

1. In the repository: **Settings** → **Pages** (left sidebar).
2. Under "Build and deployment", **Source** = **Deploy from a branch**.
3. **Branch** = `main`, **Folder** = `/ (root)`. Click **Save**.
4. Wait ~1 minute, then refresh:
   > ✅ Your site is live at `https://YOUR-USERNAME.github.io/dudka-lab-website/`

---

## 3 · Connect your custom domain

### A. Tell GitHub about the domain

The `CNAME` file in this repo already says `dudkalab.me`. If you bought a
different domain, edit the `CNAME` file so it contains **only** your domain on
a single line, no `https://`, no trailing slash:
```
dudkalab.com
```

### B. Tell the domain about GitHub

Add **DNS records** at your registrar. Open the DNS panel
(Porkbun: "DNS Records"; Namecheap: "Advanced DNS"; Cloudflare: "DNS").
**Delete any default A/AAAA/CNAME records first**, then add:

| Type  | Host (a.k.a. Name) | Value / Answer            | TTL       |
|-------|--------------------|---------------------------|-----------|
| A     | `@` (or blank)     | `185.199.108.153`         | Automatic |
| A     | `@`                | `185.199.109.153`         | Automatic |
| A     | `@`                | `185.199.110.153`         | Automatic |
| A     | `@`                | `185.199.111.153`         | Automatic |
| AAAA  | `@`                | `2606:50c0:8000::153`     | Automatic |
| AAAA  | `@`                | `2606:50c0:8001::153`     | Automatic |
| AAAA  | `@`                | `2606:50c0:8002::153`     | Automatic |
| AAAA  | `@`                | `2606:50c0:8003::153`     | Automatic |
| CNAME | `www`              | `YOUR-USERNAME.github.io.`| Automatic |

(`@` means the apex of the domain — i.e., `dudkalab.me` itself. Some registrars
don't allow `@`; just leave the field blank.)

### C. Set the custom domain in GitHub

1. Repository → **Settings** → **Pages**.
2. Under "Custom domain", type `dudkalab.me`. Click **Save**.
3. When the DNS check passes, **Enforce HTTPS** becomes available — **check it**.

### D. Wait for DNS to propagate (10–30 min, sometimes 24 h)

Check progress with:
- <https://dnschecker.org/#A/dudkalab.me> — should show GitHub's IPs everywhere.
- `dig dudkalab.me +short` (Mac/Linux) — should return GitHub's IPs.

When it's ready, `https://dudkalab.me` shows your site, with the green padlock.

---

## 4 · Editing the site after launch

### Replace a schematic

Save your SVG with the same filename as the placeholder
(e.g., `images/schematics/dir1-origin-of-evolution.svg`). The HTML doesn't
need to be edited.

### Edit the home-page paragraph

Open `index.html`, find `MAIN PARAGRAPH PLACEHOLDER`, replace the
italicized `<p>...</p>` with your text.

### Add a publication

Open `pages/publications.html`. The list is grouped into three sections —
**Research Articles**, **Methods**, **Reviews** — matching your CV. Copy any
existing `<li>…</li>` block, paste it inside the right `<ul class="pub-list">`,
and edit title / authors / journal / DOI.

If a paper is "selected" (i.e., should appear on the home page with its
schematic), also add a `<li class="with-vignette">…</li>` block to the
`Selected Publications` list inside `index.html`.

### Add a lab member

Open `pages/people.html`. Copy the commented-out block, uncomment it, fill
in name/role/photo. Drop a square JPG (≥ 360 × 360 px) into `images/`.

### Push updates

```bash
git add -A
git commit -m "Updated publications list"
git push
```

Or via the GitHub web UI: drag changed files to **Add file → Upload files**
in the repo. Changes go live within ~1 minute.

---

## 5 · Color theme

Everything is driven by CSS variables at the top of `css/style.css`:

```css
:root {
  --green:   #00b386;   /* primary accent */
  --magenta: #c850c0;   /* secondary accent */
  --blue:    #4a90d9;   /* tertiary accent */
  --hero-bg: #0c0c0c;
}
```

Change one of those values and the entire site re-themes (gradients, tags,
section underlines, buttons).

---

## 6 · Troubleshooting

| Problem | Fix |
|---|---|
| `Site not found` after enabling Pages | `index.html` must be at the repo root. |
| Custom domain shows "DNS check unsuccessful" | Wait 30 min; verify A records at <https://dnschecker.org>. |
| Images broken (404) on a sub-page | Sub-pages live in `pages/` and reference `../images/…`. Don't change those paths. |
| Lehigh logo looks too big/small in the strip | Edit `.lehigh-strip img.lehigh-logo` height in `css/style.css`. |

---

## License & credits

CSS, layout, and HTML in this repository are CC0 — use freely.
Lehigh logos belong to Lehigh University; respect their use guidelines.
Hero image, LabOverview schematic, and headshot are yours.
