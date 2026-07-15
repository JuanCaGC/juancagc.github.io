# Personal academic website

Static site for [Juan Camilo González Cabrera](https://juancagc.github.io/). Plain HTML and one CSS file. No build step, no frameworks, no JavaScript.

Live URL once deployed: **https://juancagc.github.io/**

## Contents

| Path | Purpose |
|------|---------|
| `index.html` | Single-page site |
| `style.css` | Stylesheet |
| `files/` | CV (`cv.pdf`), talk slides, portrait |

## First-time deploy on GitHub Pages

These steps assume the repository is named `juancagc.github.io` and will publish from the `master` (or `main`) branch root.

### 1. Add your files to the repo

From the project directory:

```bash
cd /path/to/juancagc.github.io
git add index.html style.css README.md files/
git commit -m "Add personal academic website"
```

### 2. Connect to GitHub (if not already)

Create an empty public repository named exactly `juancagc.github.io` under your GitHub account (`JuanCaGC` or the account that owns the `juancagc` username redirect), then:

```bash
git remote add origin https://github.com/JuanCaGC/juancagc.github.io.git
git branch -M master
git push -u origin master
```

If you prefer `main` as the default branch name, use `main` instead of `master` in every step below, and select that branch in the Pages settings.

### 3. Enable GitHub Pages

1. Open the repository on GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Branch: `master` (or `main`), folder: `/ (root)`.
5. Click **Save**.

GitHub will serve the site at `https://juancagc.github.io/` within a few minutes. There is no Actions workflow and no Jekyll/Hugo build. The `index.html` at the repository root is the homepage.

### 4. Verify

Open https://juancagc.github.io/ and confirm the page loads. Hard-refresh if an old empty site was cached.

## Updating the site later

Edit `index.html` or `style.css` locally, then:

```bash
git add -A
git commit -m "Update site content"
git push
```

Changes appear on GitHub Pages after a short delay (often under a minute).

## Adding your CV, slides, and photo

1. **CV:** place the PDF at `files/cv.pdf`. The header already links to it.
2. **Talk slides:** put PDFs or other files under `files/` (for example `files/albatross-2026-slides.pdf`) and link them from the Talks section in `index.html`.
3. **Photo:** replace `files/portrait.svg` with a photo (JPEG or PNG), then update the `src` attribute of the portrait `<img>` in `index.html` if the filename changes. Keep the image roughly square; CSS sizes it to 160px.

Commit and push after adding files, same as above.

## Local preview

Open `index.html` in a browser, or from the repo root:

```bash
python3 -m http.server 8000
```

Then visit http://localhost:8000/

## Notes

- Do not add a `Gemfile`, `_config.yml`, package.json, or build tooling. GitHub Pages for a `*.github.io` user site can serve these static files directly from the branch root.
- If GitHub treats the site as a Jekyll project and something breaks, add an empty file named `.nojekyll` at the repository root and push. This project does not need Jekyll.
