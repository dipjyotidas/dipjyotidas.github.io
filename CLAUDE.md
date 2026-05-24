# CLAUDE.md — Dipjyoti Das Portfolio Site

## Site Status: LIVE ✓

- **Live URL:** https://dipjyotidas.github.io
- **Repo:** https://github.com/dipjyotidas/dipjyotidas.github.io
- **Stack:** Jekyll + al-folio theme, hosted on GitHub Pages
- **OS:** Windows 11, Ruby 4.0.5, Bundler 4.0.4

---

## Owner Profile

- **Name:** Dipjyoti Das
- **Title:** Generative AI Architect
- **Location:** Charlotte, NC, USA
- **Current employer:** Ascendion
- **Experience:** 13+ years (2013–present)
- **Email:** dipjyoti@gmail.com
- **GitHub:** https://github.com/dipjyotidas
- **LinkedIn:** https://www.linkedin.com/in/dipjyotidas/
- **Key clients:** Charter Communications, Fannie Mae, AT&T, CareSource, Duke Energy, Brighthouse Financial
- **Impact highlights:** $240M revenue (Brighthouse), 60% support call reduction (Charter), 70% faster valuations (Fannie Mae)
- **Speaking:** AIM 2026 SFO (Session Chair), Ai4 2021, RE.WORK AI
- **Memberships:** IEEE Senior Member, SWE (in progress)

---

## How Deployment Works

1. Edit files locally
2. Run Prettier to fix formatting (see below)
3. `git add` + `git commit` + `git push origin main`
4. GitHub Actions workflow **"Deploy site"** (`.github/workflows/deploy.yml`) builds the Jekyll site and pushes to the `gh-pages` branch
5. GitHub Pages serves from `gh-pages` branch
6. Live site updates in ~2 minutes

**GitHub Actions tab:** https://github.com/dipjyotidas/dipjyotidas.github.io/actions

---

## Day-to-Day Workflow

### Making any content change

```bash
# 1. Edit the file(s)

# 2. Fix Prettier formatting (required — CI will fail without this)
npx prettier . --write

# 3. Commit and push (NO Co-Authored-By lines in commit messages)
git add <file>
git commit -m "Your message here"
git push origin main
```

### Preview locally

```bash
bundle exec jekyll serve
# Open http://127.0.0.1:4000/
```

### Adding a blog post

Create `_posts/YYYY-MM-DD-post-title.md`:

```markdown
---
layout: post
title: "Your Post Title"
date: YYYY-MM-DD
description: One-line description shown in post listings
tags: [tag1, tag2]
categories: ai-ml
---

Post content here in Markdown.
```

---

## Key Files

| File                      | Purpose                                             |
| ------------------------- | --------------------------------------------------- |
| `_config.yml`             | Site-wide settings — title, URL, blog name, plugins |
| `_pages/about.md`         | Home page — bio, profile card, expertise            |
| `_pages/cv.md`            | Experience page at `/experience/`                   |
| `_pages/talks.md`         | Speaking page at `/talks/` with YouTube embeds      |
| `_pages/mentoring.md`     | Community page at `/community/`                     |
| `_posts/`                 | Blog posts — one `.md` file per post                |
| `assets/img/prof_pic.jpg` | Profile photo (400×400px)                           |
| `assets/img/favicon.png`  | Browser tab icon — DD initials on dark background   |
| `_data/socials.yml`       | Social links — GitHub, LinkedIn, email              |

---

## Current Site Structure

**Navigation (in order):** about → experience → speaking → community → blog

**Pages hidden from nav** (exist but nav: false): publications, projects, teaching, profiles, repositories, dropdown

**Config highlights:**

- `url: https://dipjyotidas.github.io`
- `baseurl:` (empty — serves from root)
- `blog_name: AI Insights`
- `imagemagick: enabled: false` (Windows path issue — enabled in CI)
- `jekyll-jupyter-notebook` disabled (no .ipynb files used)

---

## Important Rules

1. **Never add Co-Authored-By lines** to git commit messages
2. **Always run `npx prettier . --write`** before committing — the Prettier CI check will fail otherwise
3. **Commit messages** should be plain and descriptive, no co-author attribution
4. **Profile photo** is at `assets/img/prof_pic.jpg` — 400×400px square

---

## Troubleshooting

**Prettier CI fails:** Run `npx prettier . --write` locally, commit and push the fixed files.

**Site not updating after push:** Wait 2–3 min, then open in an incognito window. GitHub Pages CDN can lag.

**`jekyll serve` fails with Jupyter error:** The `assets/jupyter/blog.ipynb` file was deleted. If it reappears, delete it again.

**Push rejected (remote has changes):** Run `git pull --rebase origin main` then push again.

**`jekyll serve` URL shows `/al-folio/`:** Restart the server — config changes require restart.

---

## Phase 5 — Custom Domain (Optional, ~$12/year)

1. Buy `dipjyotidas.com` at namecheap.com
2. Add DNS A records pointing to GitHub IPs:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
   And a CNAME: `www` → `dipjyotidas.github.io`
3. In repo Settings → Pages → Custom domain: `dipjyotidas.com` → Save → Enable HTTPS
