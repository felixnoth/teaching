# Felix Noth — teaching site

A standalone static site for GitHub Pages, matching the design of the main
personal site. No build step. Everything is plain HTML — edit and push.

Deploys as a **project page** at `https://felixnoth.github.io/teaching/`
(separate repo named `teaching`). The main site links to it from its nav.

## Structure

A landing page with one card per current course; each card links to that
course's own page.

| File | What it is |
|---|---|
| `index.html` | Landing page — the list of current courses |
| `econometrics-master.html` | Course page: Econometrics (Master) |
| `econometrics-phd.html` | Course page: Econometrics (PhD) |
| `incentives-information-finance.html` | Course page: Incentives and Information in Finance |
| `style.css` | Shared base styling (copy of the main site's stylesheet) |
| `teaching.css` | Teaching-specific styling (cards, course pages) |
| `materials/` | Drop public files here to link them |
| `.nojekyll` | Serve files as-is |

Each course page has three sections: **Overview**, **Schedule**, **Materials**.

## Edit a course

Open the course's `.html` file and edit the text directly:

- **Overview** — rewrite the paragraph under `<h2>Overview</h2>`. The italic
  `[Edit this overview…]` note is a placeholder — replace/remove it.
- **Schedule** — add or edit rows in the table:
  ```html
  <tr><td class="when">4</td><td>Your topic</td></tr>
  ```
- **Meta line** (level, term, institution, language) — edit the
  `<div class="meta-grid">` near the top.

## Add or remove a course

- **Remove:** delete that course's card in `index.html` (inside
  `<div class="course-cards">`) and, if you like, its `.html` file.
- **Add:** copy an existing course `.html` file, rename it, edit its content,
  then add a matching card in `index.html`:
  ```html
  <a class="course-card" href="new-course.html">
    <h3>Course title</h3>
    <p class="meta">Course &middot; OVGU Magdeburg &middot; <span class="term">Winter term</span></p>
    <p class="blurb">One-line description.</p>
    <p class="go">View course &rarr;</p>
  </a>
  ```
  (Also add it to the nav links in each page's `<nav>` if you want it there.)

## Link a downloadable material

1. Put the file in `materials/` (e.g. `materials/econometrics-master-syllabus.pdf`).
2. In the course page's Materials section, uncomment/add a row:
   ```html
   <li><span class="kind">PDF</span><a href="materials/econometrics-master-syllabus.pdf">Syllabus</a></li>
   ```

Note: anything committed here becomes **public**. Your working materials folder
(`~/Dropbox/teaching`) is separate and stays private — copy over only the files
you want to publish.

## Deploy to GitHub Pages (one time)

1. Create a **public** repository named `teaching`.
2. From this folder:
   ```
   cd ~/Dropbox/teaching-website
   git init
   git add .
   git commit -m "initial teaching site"
   git branch -M main
   git remote add origin https://github.com/felixnoth/teaching.git
   git push -u origin main
   ```
3. Repo **Settings → Pages** → Source "Deploy from a branch", Branch `main`,
   folder `/ (root)`, Save.
4. Live at `https://felixnoth.github.io/teaching/` in 1–2 minutes.

## Local preview

```
cd ~/Dropbox/teaching-website
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
