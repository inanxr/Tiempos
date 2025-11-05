# My Fonts via GitHub + jsDelivr (Starter)

Follow these steps **exactly** to host your fonts and use them anywhere with a single `<link>`:

---

## 1) Prepare your files
- Convert your fonts to **.woff2** (best format). If you only have .ttf/.otf, export or convert to .woff2 using your font editor or a trusted local converter.
- Rename files clearly, e.g.:
  - `MyFont-Regular.woff2`
  - `MyFont-Italic.woff2`
  - `MyFont-Bold.woff2`
  - or a single `MyFont-Variable.woff2` (variable font).

Put them into the `fonts/` folder in this repository.

---

## 2) Update `fonts.css`
- Open `fonts.css` and replace the file names with your actual names.
- If you use a **variable font**, comment out the static blocks and **uncomment** the variable block. Update the weight range (e.g. `100 900`).

---

## 3) Create a GitHub repository and push
Option A — **GitHub website UI** (no CLI needed)
1. Create a new public repo on GitHub (e.g. `my-fonts`).
2. Upload these files/folders from this starter:
   - `fonts.css`
   - `index.html` (for testing)
   - `fonts/` (your .woff2 files inside)
3. Commit to the **main** branch.

Option B — **Git command line**
```bash
git init
git add .
git commit -m "Initial fonts CDN"
git branch -M main
git remote add origin https://github.com/REPLACE_WITH_YOUR_GITHUB_USERNAME/REPLACE_WITH_YOUR_REPO.git
git push -u origin main
```

---

## 4) Link your CSS via jsDelivr
Use this pattern (replace the placeholders):  
```
https://cdn.jsdelivr.net/gh/REPLACE_WITH_YOUR_GITHUB_USERNAME/REPLACE_WITH_YOUR_REPO@main/fonts.css
```
**Add to any website's `<head>`:**
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/REPLACE_WITH_YOUR_GITHUB_USERNAME/REPLACE_WITH_YOUR_REPO@main/fonts.css">
```

**(Optional) Pin to a specific commit for stability:**
1. Open your repo on GitHub → press `Y` (or copy the URL with the full commit SHA shown in the file view).
2. Replace `@main` with `@COMMIT_SHA`:
```
https://cdn.jsdelivr.net/gh/USER/REPO@COMMIT_SHA/fonts.css
```

**(Optional) Cache-bust** when you change fonts.css (so visitors get the latest):
```
.../fonts.css?v=2
```

---

## 5) Use the font in your CSS
```css
body {
  font-family: 'MyFont', system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
}
/* For variable font sample:
body { font-family: 'MyFontVF', system-ui, -apple-system, Segoe UI, Roboto, sans-serif; }
*/
```

---

## 6) Test quickly
- Open `index.html` directly (local) to preview your fonts.
- Or visit `https://cdn.jsdelivr.net/gh/USER/REPO@main/index.html` (note: HTML via jsDelivr works, but use it only for quick tests).

---

## Notes
- **CORS**: jsDelivr serves with proper CORS headers; you can use the CSS cross-site without extra server config.
- **Privacy/licensing**: Only publish fonts you have rights to distribute. For public repos, your font files are downloadable by anyone.
- **Formats**: `.woff2` is enough for modern browsers. Add `.woff` for older browser support if you must.
