# www.devharsh.me

Personal academic and industry portfolio for **Devharsh Trivedi, Ph.D., CISSP**. A hand-built static site (plain HTML + one CSS file, no build step), designed to serve both academic search committees (assistant professor) and industry hiring managers (research engineer).

## Pages

| File | Purpose |
|------|---------|
| `index.html` | Hero homepage: pitch, two-track framing, about, connect |
| `research.html` | Research agenda, publications grouped by topic, books, dissertation, awards |
| `experience.html` | Industry roles (Oracle, Philips, EClinicalWorks) and academic/research roles |
| `teaching.html` | Teaching philosophy, courses, CTF mentoring, open educational resources |
| `projects.html` | Open-source software (chiku, VaultBox, TeX Viewer Online, com-puter-tips tools) |
| `blog.html` | Links to the Blogger blog and Computer Tips, with curated posts |
| `cv.html` | HTML CV with PDF download and all profile links |
| `404.html` | Not-found page |
| `assets/style.css` | Shared stylesheet (classic professional theme) |
| `assets/Devharsh_Trivedi_CV.pdf` | Downloadable CV |
| `CNAME` | Custom domain (`www.devharsh.me`) |

## Preview locally

```bash
cd devharsh.github.io
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a public repo named **`devharsh.github.io`** under `github.com/devharsh`.
2. Push the contents of this folder to the `main` branch:
   ```bash
   cd devharsh.github.io
   git init && git add -A && git commit -m "Launch portfolio site"
   git branch -M main
   git remote add origin https://github.com/devharsh/devharsh.github.io.git
   git push -u origin main
   ```
3. In the repo: **Settings -> Pages -> Build and deployment -> Source: Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Under **Custom domain**, confirm `www.devharsh.me` (the `CNAME` file already sets this). After DNS verifies, tick **Enforce HTTPS**.

## DNS (move www.devharsh.me from Blogger to GitHub Pages)

At your domain registrar / DNS host, replace the existing Blogger records:

- **CNAME** record: host `www` -> value `devharsh.github.io`
- **CNAME** record: host `blog` -> value `ghs.google.com` (keeps your Blogger blog live at `blog.devharsh.me`; set the matching custom domain inside Blogger settings)
- **Apex** (`devharsh.me`) to redirect to `www`, add the four GitHub Pages **A** records:
  `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
  (and the matching AAAA records if you want IPv6). Verify the current IPs in the GitHub Pages docs before applying.

DNS changes can take up to 24-48 hours to propagate. Your Blogger blog stays live at its own address; this site only links out to it.

## Editing notes

- Profile photo: save your headshot as `assets/profile.jpg`. The homepage loads it automatically inside a navy circle and falls back to a "DT" monogram if the file is missing. No code change needed.
- Navigation and footer are repeated in each HTML file (no build step). If you add a page, update the `<nav>` block in each file.
- The Teaching, Research, and Diversity statement PDFs are **not** published here because they contain a home address and a personal email; the site uses `Washington, D.C., 20003` and `hi@devharsh.me`. Add redacted versions to `assets/` and link them if you want them public.
- Publication and award details are taken from the CV and verified public profiles. No counts or papers are fabricated.
