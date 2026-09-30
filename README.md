# MatAnyone-E project page

Static site with no build step and no server code. Everything the page needs is in this folder (about 30 MB).

```
index.html          the page
v/                  videos: speed race + 5 results (web previews, H.264)
t/                  poster and thumbnails
gate/               "Where the computation goes" widget: frames + data.js
fig/method.png      method figure
.nojekyll           tells GitHub Pages to serve the files as they are
```

## View it locally

- Double-click `index.html`: it opens in the browser and everything works, including the videos and the interactive gate widget.
- Or serve the folder, which is closer to how it behaves online:

  ```bash
  cd matanyone_e_projpage_site
  python3 -m http.server 8000      # then open http://localhost:8000
  ```

To send it to someone, send `matanyone_e_projpage_site.zip`. They unzip it and double-click `index.html`.

## Put it on GitHub Pages

Option A, a repository of its own. The page will be at `https://<user>.github.io/<repo>/`.

```bash
cd matanyone_e_projpage_site
git init -b main
git add .
git commit -m "MatAnyone-E project page"
git remote add origin git@github.com:<user>/<repo>.git
git push -u origin main
```

Then in the repository go to Settings → Pages → Build and deployment. Set Source to "Deploy from a branch", Branch to `main`, and folder to `/ (root)`, then Save. The site goes live after a minute or two.

Option B, inside an existing `<user>.github.io` site, the way MatAnyone and MatAnyone 2 live under
`pq-yang.github.io/projects/...`:

1. Copy this folder to `projects/MatAnyone-E/` in that repository, then commit and push.
2. The page is at `https://<user>.github.io/projects/MatAnyone-E/`.
3. In `index.html`, the "More Research" links can then be relative paths (`/projects/MatAnyone2/`, `/projects/MatAnyone/`), exactly like the other two pages.

Limits to keep in mind:
- A single file must be under 100 MB. The largest here is about 5 MB.
- The whole site should stay under 1 GB.
- Bandwidth has a soft limit of 100 GB a month.
- Do not use Git LFS for the videos: GitHub Pages does not serve LFS files.

## Still to fill in (search `index.html`)

- `href="#" class="au"`: the six author homepage links.
- `native:''` in the `CLIPS` list: the link behind the "Watch in native …" button, one per result, once the 4K files are hosted (for example on Hugging Face).
- `class="navicon" href="#"`: the home icon in the top bar.
- The Paper / Code buttons ("soon") and the BibTeX block.

## Rebuilding

This folder is generated from the working copy in `matanyone_e_projpage_v2/` with `python build_site.py`. Edit that copy, then rebuild.
