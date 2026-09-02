# imranrimon.github.io

Personal academic website for **Muhammad Imran Hossain** — a single, self-contained `index.html` (all CSS/JS inline, no build step, no frameworks). It deploys on GitHub Pages exactly as written.

## Files

- `index.html` — the entire site.
- `photo.jpg` — hero portrait (square image works best; shown as a circle). Keep the name `photo.jpg` (lowercase — GitHub Pages is case-sensitive).
- `README.md` — this file.

> **CV / `cv.pdf`:** intentionally omitted, and the "Download CV" button removed, for double-blind-review safety — a public CV listing under-review work would de-anonymize your submissions. See "Adding a CV later" below.

---

## Deploy as a USER site → https://imranrimon.github.io

A user (or "root") site lives at `https://<username>.github.io` and must use a repo named exactly `<username>.github.io`.

1. **Create the repo.** On GitHub, create a new **public** repository named exactly:

   ```
   imranrimon.github.io
   ```

   (Do not add a README/license from the UI if you plan to push these files — keep it empty.)

2. **Add your files locally and push to `main`:**

   ```bash
   git init
   git branch -M main
   git add index.html photo.jpg README.md
   git commit -m "Initial site"
   git remote add origin https://github.com/imranrimon/imranrimon.github.io.git
   git push -u origin main
   ```

3. **Enable Pages.** In the repo: **Settings → Pages → Build and deployment**.
   - **Source:** *Deploy from a branch*
   - **Branch:** `main` and folder `/ (root)` → **Save**.

4. Wait ~1 minute, then open **https://imranrimon.github.io**. It's live.

> Because the file is named `index.html` at the repo root, GitHub Pages serves it automatically — no configuration or Jekyll needed.

---

## Alternative: deploy as a PROJECT site

If you'd rather host it under an existing account at a sub-path (e.g. `https://imranrimon.github.io/website/`):

1. Create/choose any public repo (e.g. `website`) and push `index.html` and `photo.jpg` to `main`.
2. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`.**
3. Your site will be at `https://imranrimon.github.io/website/`.

All links in this page are relative (`cv.pdf`) or absolute (`https://…`), so it works under a sub-path with no changes.

---

## Add a custom domain (optional)

1. Buy a domain and, at your DNS provider, point it at GitHub Pages:
   - **Apex domain** (`example.com`): add four `A` records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (and optionally `AAAA` records for IPv6).
   - **Subdomain** (`www.example.com`): add a `CNAME` record → `imranrimon.github.io`.
2. In **Settings → Pages → Custom domain**, enter your domain and **Save**. GitHub commits a `CNAME` file to the repo automatically.
3. Tick **Enforce HTTPS** once the certificate is issued.

> You can also add the `CNAME` file yourself: create a file named `CNAME` (no extension) at the repo root containing a single line with your domain, e.g. `www.example.com`.

---

## Adding a CV later (blind-safe)

The CV is intentionally omitted for now (double-blind review). To add one **after** the under-review work is accepted — or a **blind-safe** version (under-review items removed) sooner:

1. Put `cv.pdf` in the **same folder as `index.html`** (repo root).
2. Re-add the "Download CV" button as the first item in `.btn-row` in `index.html`:

   ```html
   <a class="btn btn-primary" href="cv.pdf" aria-label="Download CV as PDF">
     <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>
     Download CV
   </a>
   ```

   Then change the Email button back from `class="btn btn-primary"` to `class="btn"`.
3. Commit `cv.pdf` and push.

---

## Local preview

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Editing tips

- **Colors / dark mode:** edit the CSS custom properties in the `:root` and `[data-theme="dark"]` blocks at the top of the `<style>` tag.
- **Fonts:** the page loads *Newsreader* (serif headings) + *Inter* (sans body) from Google Fonts, and falls back to Georgia / system sans if offline.
- **Content:** each section is plain semantic HTML — update the text directly. Project cards carry `data-cat` classes (`funded`, `genai`, `cps`, `health`) that drive the filter buttons.
