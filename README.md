# My Fonts via GitHub + jsDelivr (Starter)

Host all your custom fonts — like **Tiempos**, **Gill Sans Pro**, **Futura LT**, **Inter**, **Helvetica**, and more — directly from GitHub and use them anywhere on the web with a single `<link>` tag.

---

## 1) Prepare your font files

✅ **Recommended format:** `.woff2`  
If your fonts are `.otf` or `.ttf`, convert them locally using your font editor or a trusted converter.

Use clear names for each weight and style, for example:
```

MyFont-Regular.woff2
MyFont-Italic.woff2
MyFont-Bold.woff2
MyFont-Variable.woff2  ← (for variable fonts)

```

Organize fonts in folders like this:
```

fonts/
├── TiemposText/
├── TiemposHeadline/
├── TiemposFine/
├── Gill Sans Pro/
├── Futura LT/
├── Helvetica/
├── Inter/
└── etc.

````

---

## 2) Edit `fonts.css`

Open `fonts.css` and make sure:
- Each `@font-face` block points to the correct file paths (e.g. `./fonts/TiemposText/TiemposText-Regular.otf`).
- If you’re using variable fonts, **comment out** the static sections and **uncomment** the variable ones.
- The `:root` block at the bottom defines CSS variables like:
  ```css
  :root {
    --tiempos-text: 'Tiempos Text', serif;
    --helvetica: 'Helvetica LT Std', Arial, sans-serif;
    --inter: 'Inter', system-ui, sans-serif;
  }
````

---

## 3) Create a GitHub repository and push

### Option A — GitHub UI (no CLI)

1. Create a new **public** repo (e.g. `fonts-cdn`).
2. Upload these:

   * `fonts.css`
   * `index.html` (for demo)
   * `fonts/` folder (with all your font files)
3. Commit to the **main** branch.

### Option B — Command Line

```bash
git init
git add .
git commit -m "Initial fonts CDN setup"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

---

## 4) Link your hosted CSS via jsDelivr

You can now load your fonts anywhere with:

```
https://cdn.jsdelivr.net/gh/YOUR_USERNAME/YOUR_REPO@main/fonts.css
```

### Example:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/inanxr/Tiempos@main/fonts.css">
```

**(Optional)** Pin to a specific commit for stability:

1. Open your repo → press **Y** on GitHub to freeze the commit URL.
2. Replace `@main` with your commit SHA:

   ```
   https://cdn.jsdelivr.net/gh/YOUR_USERNAME/YOUR_REPO@COMMIT_SHA/fonts.css
   ```

**(Optional)** Cache-bust when you update:

```
.../fonts.css?v=2
```

---

## 5) Use the fonts in your website

```css
body {
  font-family: 'Tiempos Text', serif;
}

h1 {
  font-family: 'Tiempos Headline', serif;
  font-weight: 700;
}

.nav {
  font-family: 'Gill Sans Pro', sans-serif;
}

.smallprint {
  font-family: 'Inter', system-ui, sans-serif;
  font-size: 0.875rem;
}
```

Or use your global variables defined in `:root`:

```css
body { font-family: var(--tiempos-text); }
h2  { font-family: var(--helvetica); }
```

---

## 6) Quick testing

* Open `index.html` locally to preview your setup.
* Or test it live:

  ```
  https://cdn.jsdelivr.net/gh/YOUR_USERNAME/YOUR_REPO@main/index.html
  ```

*(Note: jsDelivr serves HTML fine for testing, but don’t use it for production sites.)*

---

## Notes

* **CORS:** jsDelivr is already CORS-enabled, so your fonts will load cross-domain automatically.
* **Licensing:** Only publish fonts you have redistribution rights for.
  Commercial fonts (e.g. Helvetica, Futura LT, Garamond Premier, Neo Sans, Gill Sans Pro) should remain private or be hosted under license.
* **Performance:** `.woff2` is ideal for web delivery — smaller and faster.
  You can keep `.otf` for full-quality backups or local use.
* **Cache:** jsDelivr caches aggressively; use versioned URLs when you update fonts.

---

**Enjoy your personal Google-Fonts-style CDN** — fully powered by GitHub + jsDelivr 🚀
All you need is one link:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/inanxr/Tiempos@main/fonts.css">
```