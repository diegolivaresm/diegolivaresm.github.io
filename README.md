# Academic website — Diego Livares

Personal academic site built with [Quarto](https://quarto.org), deployed to GitHub Pages.

## Prerequisites

1. **Quarto** installed: <https://quarto.org/docs/get-started/> (recent RStudio bundles it).
2. **RStudio** (recommended) or any editor.
3. **multibib extension** (needed for the split Publications page). From the project
   folder, in the Terminal:
   ```bash
   quarto add pandoc-ext/multibib
   ```
   This creates an `_extensions/` folder — commit it to the repo.

## Structure

```
.
├── _quarto.yml          # Global config: navbar, links (ORCID, GitHub, Dataverse), theme
├── index.qmd            # Home / landing (bio + research interests)
├── publications.qmd     # Papers / Reports / Databases (each from its own .bib)
├── experience.qmd       # Education / Awards / Conferences
├── bib/
│   ├── papers.bib       # Journal articles, chapters
│   ├── reports.bib      # Research reports
│   └── databases.bib    # Published datasets (Dataverse)
├── apa.csl              # APA citation style
├── styles.scss          # Palette and typography
├── assets/              # profile.jpg, favicon.png, cv.pdf (replace placeholders)
└── .github/workflows/   # Auto-publish on each push
```

## Three tabs

- **Home** — landing page with your bio and research interests.
- **Publications** — three sections (Papers, Reports, Databases). Each pulls from
  its matching file in `bib/`. To add a publication, drop a BibTeX entry into the
  right file and re-render — it appears automatically.
- **Experience** — Education, Awards, Conferences (plain Markdown; edit directly).

## Customise

1. Replace placeholders in `_quarto.yml` and `index.qmd`: your real ORCID,
   Dataverse URL, and email.
2. Put real files in `assets/`: `profile.jpg`, `favicon.png`, `cv.pdf`.
3. Add your publications to the files in `bib/` (export BibTeX from Zotero or
   Google Scholar).
4. Fill in `experience.qmd`.

## Preview locally

Open `diego-website.Rproj` in RStudio and hit **Render**, or in the Terminal:

```bash
quarto preview
```

## Publish to GitHub Pages

### Option A — automatic (recommended, already configured)
1. Create a new repo, e.g. `diegolivaresm.github.io`.
2. Push the project:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/diegolivaresm/YOUR-REPO.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → branch `gh-pages`**.
4. Every push to `main` re-renders and republishes automatically.

### Option B — manual from RStudio
```bash
quarto publish gh-pages
```

## URL note

- If the repo is `diegolivaresm.github.io`, the site lives at `https://diegolivaresm.github.io`.
- Any other name → `https://diegolivaresm.github.io/YOUR-REPO/`. Adjust `site-url` in `_quarto.yml` accordingly.

## Citation style

The site uses APA (`apa.csl`). To switch to Chicago (Quarto's default), delete the
`csl: apa.csl` line in `publications.qmd`.
