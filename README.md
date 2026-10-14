# CFD Portfolio — Ananth Narayan

Hugo-based portfolio site hosted on GitHub Pages.  
Live: **https://ananth-narayan-iitm.github.io**

---

## Quick start (local preview)

### 1. Install Hugo extended

```bash
# Download the extended binary (needed for SCSS/CSS processing)
wget -O /tmp/hugo.tar.gz https://github.com/gohugoio/hugo/releases/download/v0.128.2/hugo_extended_0.128.2_linux-amd64.tar.gz
tar -xzf /tmp/hugo.tar.gz -C /tmp/ hugo
sudo mv /tmp/hugo /usr/local/bin/hugo
hugo version   # should show "extended"
```

### 2. Preview locally

```bash
cd cfdPortfolio
hugo server -D --open
# → http://localhost:1313
```

Changes hot-reload automatically.

---

## Deploy to GitHub Pages (one-time setup)

### Step 1 — Create the repository

1. Go to https://github.com/new
2. Repository name: **`Ananth-Narayan-IITM.github.io`** (exact — this gives you a user site)
3. Visibility: Public
4. **Do not** initialise with README

### Step 2 — Enable Pages via GitHub Actions

1. Push the repo (Step 3 below)
2. On GitHub → **Settings → Pages**
3. Source: **GitHub Actions**
4. Save

### Step 3 — Push for the first time

```bash
cd cfdPortfolio
git init
git add .
git commit -m "Initial portfolio commit"
git branch -M main
git remote add origin https://github.com/Ananth-Narayan-IITM/Ananth-Narayan-IITM.github.io.git
git push -u origin main
```

The GitHub Actions workflow (`.github/workflows/hugo.yml`) will automatically:
- Install Hugo extended
- Build the site
- Deploy to `https://ananth-narayan-iitm.github.io`

Every subsequent `git push` triggers a redeploy.

---

## Adding your content

### Adding a CFD result image

1. Put your ParaView screenshot (PNG/JPG) in `static/images/`, e.g. `static/images/channel-flow.png`
2. In the project's front matter, add `image: "/images/channel-flow.png"`

### Adding an OpenFOAM project

Create `content/projects/openfoam/channel-flow.md`:

```yaml
---
title: "Turbulent Channel Flow Re_τ = 395"
date: 2024-10-01
description: "LES simulation benchmarked against Kim et al. DNS data."
image: "/images/channel-flow.png"
tags: ["LES", "turbulence", "benchmark"]
---

Write your project description here in Markdown.
Include equations with $...$, results, methodology.
```

Same pattern for `dafoam/`, `basilisk/`, `code/`.

### Adding a Note (with math)

Create `content/notes/my-note.md`:

```yaml
---
title: "Title of your derivation"
date: 2024-10-14
category: "Derivation"   # Derivation | Method | Theory | Review
description: "One line summary"
tags: ["tag1", "tag2"]
---

Inline math: $\nabla \cdot \mathbf{v} = 0$

Display math:
$$\frac{\partial \mathbf{v}}{\partial t} + \mathbf{v} \cdot \nabla\mathbf{v} = -\frac{1}{\rho}\nabla p + \nu\nabla^2\mathbf{v}$$
```

KaTeX renders automatically on all `/notes/` pages.

### Updating contact / hobbies

Edit `themes/cfd-theme/layouts/contact/list.html` directly — it's a static layout, not data-driven.

### Adding your photo

1. Add `static/images/profile.jpg` (portrait, ≈ 300×400 px)
2. In `content/about/_index.md`, uncomment: `# photo: "/images/profile.jpg"`

### Setting up the contact form

1. Register free at https://formspree.io
2. Create a form → copy the endpoint ID (looks like `xpzgkwrd`)
3. In `themes/cfd-theme/layouts/contact/list.html`, replace `YOUR_FORM_ID` with your ID

---

## Site structure

```
content/
├── _index.md              ← home
├── projects/
│   ├── openfoam/          ← add .md files here for each simulation
│   ├── dafoam/
│   ├── basilisk/
│   └── code/
├── about/_index.md        ← edit your bio here
├── publications/_index.md ← edit your papers here (raw HTML in Markdown)
├── skills/_index.md       ← blank (layout is hardcoded in the theme)
├── notes/                 ← add .md files for each note/derivation
└── contact/_index.md      ← blank (layout is in the theme)

themes/cfd-theme/
├── layouts/               ← all HTML templates
├── static/css/main.css    ← all styles (CSS custom properties — dark theme)
└── static/js/main.js      ← minimal JS (nav, skill bar animation)
```

---

## Updating skill bars

Open `themes/cfd-theme/layouts/skills/list.html` and adjust the `width:` values in each `.skill-bar__fill` style attribute (e.g. `style="width:85%"`).

## Changing colors

All colors are CSS custom properties in `themes/cfd-theme/static/css/main.css` under `:root {}`. The main ones:

| Variable | Default | Meaning |
|----------|---------|---------|
| `--c-fluid` | `#00d4ff` | Cyan accent — fluid |
| `--c-heat` | `#ff6b35` | Orange accent — heat |
| `--c-gold` | `#ffd700` | Gold — optimization |
| `--bg-primary` | `#0a0e1a` | Page background |
