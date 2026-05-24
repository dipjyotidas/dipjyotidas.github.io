# CLAUDE.md — Dipjyoti Das Personal Portfolio Site

## Project Overview

Build and deploy a personal portfolio website for **Dipjyoti Das**, a Generative AI Architect with 13+ years of AI/ML experience. The site uses **Jekyll** with the **al-folio** theme, hosted on **GitHub Pages** for free.

- **GitHub:** https://github.com/dipjyotidas
- **LinkedIn:** https://www.linkedin.com/in/dipjyotidas/
- **Target repo name:** `dipjyotidas.github.io`
- **OS:** Windows

---

## Phase 1 — Prerequisites (Run Once)

### 1.1 Install Ruby (required for Jekyll)

Jekyll runs on Ruby. On Windows, use RubyInstaller.

1. Go to https://rubyinstaller.org/downloads/
2. Download **Ruby+Devkit 3.2.x (x64)** — the recommended version with Devkit
3. Run the installer — keep all default options checked
4. At the end, a terminal window opens asking which components to install — type `1` and press Enter, then wait for it to finish
5. Close and reopen your terminal, then verify:

```bash
ruby --version
gem --version
```

Both should return version numbers.

### 1.2 Install Jekyll and Bundler

```bash
gem install jekyll bundler
jekyll --version
```

### 1.3 Install Git (if not already installed)

Check first:

```bash
git --version
```

If not installed, download from https://git-scm.com/download/win and install with default options.

### 1.4 Configure Git with your identity

```bash
git config --global user.name "Dipjyoti Das"
git config --global user.email "dipjyoti@gmail.com"
```

### 1.5 Install VS Code extensions (optional but helpful)

Open VS Code, go to Extensions (Ctrl+Shift+X), and install:

- **Jekyll Snippets** — syntax help for Jekyll files
- **Markdown All in One** — for writing blog posts
- **GitLens** — better Git integration

---

## Phase 2 — Create the GitHub Repository

### 2.1 Fork the al-folio theme

1. Go to https://github.com/alshedivat/al-folio
2. Click **Fork** (top right)
3. Under "Repository name", type exactly: `dipjyotidas.github.io`
4. Click **Create fork**

This is now your site repo at: https://github.com/dipjyotidas/dipjyotidas.github.io

### 2.2 Enable GitHub Pages

1. In your forked repo, go to **Settings** → **Pages**
2. Under "Source", select **GitHub Actions**
3. Save

### 2.3 Clone the repo to your machine

Open a terminal in the folder where you want to keep your projects (e.g. `C:\Projects\`) and run:

```bash
git clone https://github.com/dipjyotidas/dipjyotidas.github.io.git
cd dipjyotidas.github.io
```

### 2.4 Install dependencies

```bash
bundle install
```

This installs all the Ruby gems the theme needs. May take a few minutes.

### 2.5 Preview the site locally

```bash
bundle exec jekyll serve
```

Open your browser and go to: http://localhost:4000

You should see the default al-folio site. Now we'll replace it with your content.

---

## Phase 3 — Personalise the Site

All personalisation happens in `_config.yml` and the content files. Claude should edit these files directly.

### 3.1 Edit `_config.yml`

Replace the relevant fields with Dipjyoti's information:

```yaml
# Site settings
title: Dipjyoti Das
first_name: Dipjyoti
middle_name:
last_name: Das
email: dipjyoti@gmail.com
description: >
  Generative AI Architect | 13+ Years in AI/ML | Agentic AI, RAG, LLMs |
  Speaker at AIM 2026, Ai4 | Charlotte, NC
keywords: generative AI, machine learning, agentic AI, RAG, LLM, AI architect, data science
lang: en

url: https://dipjyotidas.github.io
baseurl:

# Social links
github_username: dipjyotidas
linkedin_username: dipjyotidas

# Repository for edit links
repo: https://github.com/dipjyotidas/dipjyotidas.github.io

# Theme settings
theme_color: blue # options: blue, pink, red, yellow, purple
enable_darkmode: true

# Blog settings
blog_name: AI Insights
blog_description: Thoughts on Generative AI, Agentic Systems, and Production ML

# SEO
og_image: /assets/img/profile.jpg

# Analytics (add your Google Analytics ID later)
# google_analytics: G-XXXXXXXXXX
```

### 3.2 Edit `_pages/about.md` — Home / Hero page

Replace the content with:

```markdown
---
layout: about
title: about
permalink: /
subtitle: >
  Generative AI Architect · 13+ Years in AI/ML · Charlotte, NC
  <br>
  <a href="https://www.linkedin.com/in/dipjyotidas/">LinkedIn</a> ·
  <a href="https://github.com/dipjyotidas">GitHub</a>

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false
  more_info: >
    <p>Charlotte, NC, USA</p>
    <p>Gen AI Architect @ Ascendion</p>
    <p>IEEE Senior Member</p>

news: false
selected_papers: false
social: true
---

I am a Generative AI Architect with 13+ years of hands-on experience delivering
end-to-end AI/ML and Data Science solutions across startups and Fortune 150
companies spanning Tech, Finance, Utilities, Healthcare, Insurance, Telecom,
and Logistics.

Currently at **Ascendion**, I lead architecture and production deployment of
large-scale Agentic AI systems — including a unified chatbot serving 80,000+
field technicians at Charter Communications and an AI-powered discharge
automation system at CareSource.

My work has generated measurable enterprise impact: **$240M in incremental
annual revenue** at Brighthouse Financial, **60% reduction in support calls**
at Charter Communications, and **70% faster valuation approvals** at Fannie Mae.

I am passionate about moving AI from prototype to production — designing systems
that are robust, observable, and actually useful in the real world.

**Areas of expertise:** Agentic AI · RAG systems · LLMOps · Generative AI
architecture · MLOps · Cloud AI (AWS, Azure, GCP) · Python · LangGraph ·
LangChain · Kubernetes
```

### 3.3 Add profile photo

- Add your professional photo to `assets/img/` as `prof_pic.jpg`
- Recommended size: 400×400px, square crop

### 3.4 Edit `_pages/cv.md` — Experience page

```markdown
---
layout: page
permalink: /experience/
title: experience
description: 13+ years of AI/ML across enterprise and startup environments
nav: true
nav_order: 2
---

## Work Experience

### Gen AI Architect — Ascendion, Charlotte NC

**Oct 2025 – Present**

- Led architecture and deployment of a unified Agentic AI chatbot on AWS EKS
  serving 80,000+ field technicians at Charter Communications
- Architected LangGraph-based orchestration with role/intent-aware routing;
  reduced support calls by 60% with million-dollar savings
- Designed Agentic AI solution for CareSource to automate discharge log intake
  using Azure Document Intelligence and LLM validation (HITL)
- Built RAG service embedding 1,000+ Confluence pages and 5,000+ technical
  attachments into PGVector DB

---

### AI Architect/Engineer — CGI Technologies, Charlotte NC

**June 2023 – Oct 2025**

- Built CGI Pulse AI GenAI platform with self-hosted LLMs (Llama/Mixtral via vllm)
  and advanced RAG on Azure Kubernetes Service
- Served as AI Architect for Fannie Mae's Enterprise Gen AI team; defined GenAI
  roadmap across business units
- Built Agentic AI system reducing Foreclosed Property Valuation approval time by 70%
- Developed multi-agent workflows for AT&T's Ask ATT customer service platform

---

### Staff Data Scientist — One Concern, Menlo Park CA

**Nov 2021 – May 2023**

Climate risk analytics startup. Delivered Resilience and Business Interruption
scores for US/Japan commercial properties integrated into Swiss RE CatNet and
Willis Tower Watson platforms.

---

### Data Scientist II — Duke Energy, Charlotte NC

**Mar 2019 – Nov 2021**

- Built time-series forecasting models (LSTM, CNN1D, SARIMA) for operational planning
- Developed Gaussian Mixture Model to recommend commercial properties for Energy
  Efficiency programs; estimated impact $8–10M/year
- Built Risk Propensity ML model to score customers by delinquency likelihood;
  estimated impact $5.1M/year

---

### Data Scientist II — Brighthouse Financial, Charlotte NC

**June 2017 – Jan 2019**

- Built 3-layer stacked ensemble Propensity model for annuity product targeting
- Impact: **$240M in incremental annual revenue** ($60M per quarter)
- Led ML model migration to SAP cloud; built ML and ETL pipelines with PySpark

---

### Decision Specialist — R+L Carriers, Ocala FL

**March 2013 – June 2017**

- Built Time Series Forecasting models (Holt-Winters, ETS, ARIMA) for revenue
  and shipment prediction
- Automated forecasting pipeline; saved $800K/year by eliminating manual effort

---

## Education

**MS, Materials Science and Engineering** — University of Florida, 2012 (GPA 3.9/4)

**BTech, Metallurgical & Materials Engineering** — NIT Trichy, India, 2010 (GPA 8.3/10)

**Certifications:** AWS ML Specialty · AWS Solutions Architect Associate (in progress)

**Courses:** Machine Learning (Stanford) · Data Science: Data to Insights (MIT)
```

### 3.5 Edit `_pages/talks.md` — Speaking page

```markdown
---
layout: page
permalink: /talks/
title: speaking
description: Conference talks and session leadership on production AI systems
nav: true
nav_order: 3
---

## Conference Speaking

### AIM 2026 — San Francisco

**Session Chair and Speaker**
_Topic: Production-scale Agentic AI Systems in the Enterprise_

<div class="video-container">
  <iframe width="560" height="315"
    src="https://www.youtube.com/embed/zOum0De_6K0"
    title="AIM 2026 Talk - Dipjyoti Das"
    frameborder="0"
    allowfullscreen>
  </iframe>
</div>

---

### Ai4 2021 — Speaker

_Topic: AI/ML in Enterprise_

<div class="video-container">
  <iframe width="560" height="315"
    src="https://www.youtube.com/embed/K_5Ij0OawjI"
    title="Ai4 2021 Talk - Dipjyoti Das"
    frameborder="0"
    allowfullscreen>
  </iframe>
</div>

---

### RE.WORK AI — Speaker

<div class="video-container">
  <iframe width="560" height="315"
    src="https://www.youtube.com/embed/yMOUTPyAyYU"
    title="RE.WORK AI Talk - Dipjyoti Das"
    frameborder="0"
    allowfullscreen>
  </iframe>
</div>

<style>
.video-container { margin: 1.5rem 0; }
.video-container iframe { max-width: 100%; border-radius: 8px; }
</style>
```

### 3.6 Create `_pages/mentoring.md` — Mentoring & Community page

Create this file at `_pages/mentoring.md`:

```markdown
---
layout: page
permalink: /community/
title: community
description: Mentoring, judging, and giving back to the AI/ML community
nav: true
nav_order: 4
---

## Mentoring

### Great Learning / UT Austin — AIML Program Mentor

Selected after a technical demo and interview process to mentor a cohort of
~20 working professionals in the Post-Graduate AI/ML program. Conducted weekly
sessions covering AI/ML, NLP, and Data Science. Evaluated assignments and
capstone projects. Guided practical Python and ML implementations.

---

## Judging & Evaluation

### Pinnacle Solutions Group Hackathon 2026 — Judge

_Charlotte, NC_
Evaluated AI and software engineering projects in the AI-Augmented Engineering
Excellence category. Reviewed demo quality, technical execution, AI-assisted
development practices, innovation, and implementation.

[LinkedIn post](https://www.linkedin.com/feed/update/urn:li:activity:7459010153804152832/)

### Technovation Girls — Judge _(in progress)_

### Society of Women Engineers (SWE) India — Scholarship Reviewer

Reviewed and evaluated undergraduate STEM scholarship applications.

---

## Memberships

- **IEEE Senior Member**
- **IEEE Charlotte Chapter** — active participant
- **Society of Women Engineers** — Senior Membership _(in progress)_
```

### 3.7 Update navigation in `_data/navigation.yml`

Ensure the nav includes your pages:

```yaml
- name: about
  url: /
- name: experience
  url: /experience/
- name: speaking
  url: /talks/
- name: community
  url: /community/
- name: blog
  url: /blog/
```

### 3.8 Write your first blog post

Create `_posts/2026-05-23-production-agentic-ai.md`:

```markdown
---
layout: post
title: "What it actually takes to deploy Agentic AI in the enterprise"
date: 2026-05-23
description: Lessons from building production Agentic AI systems at scale
tags: [agentic-ai, production, enterprise, langgraph]
categories: ai-ml
---

Your first post content here. Write in Markdown.
This is where your thought leadership content lives.
```

---

## Phase 4 — Deploy to GitHub Pages

### 4.1 Stage, commit and push

```bash
git add .
git commit -m "Initial site setup with personal content"
git push origin main
```

### 4.2 Watch the build

Go to your repo on GitHub → **Actions** tab. You'll see a workflow running called "Deploy Jekyll site". It takes 1–3 minutes. When the green checkmark appears, your site is live at:

**https://dipjyotidas.github.io**

---

## Phase 5 — Connect a Custom Domain (Optional, ~$12/year)

### 5.1 Buy a domain

Go to https://www.namecheap.com and buy `dipjyotidas.com` (or `dipjyoti.ai` if available).

### 5.2 Add DNS records in Namecheap

In Namecheap DNS settings, add these A records pointing to GitHub:

```
A  @  185.199.108.153
A  @  185.199.109.153
A  @  185.199.110.153
A  @  185.199.111.153
CNAME  www  dipjyotidas.github.io
```

### 5.3 Add custom domain in GitHub

1. Go to repo **Settings** → **Pages**
2. Under "Custom domain", type: `dipjyotidas.com`
3. Click Save
4. Check "Enforce HTTPS" once it appears

DNS propagation takes 10–30 minutes.

---

## Day-to-Day Workflow (After Setup)

To add a new blog post:

```bash
# 1. Create a new file in _posts/
# File name format: YYYY-MM-DD-title-of-post.md

# 2. Add content in Markdown

# 3. Preview locally
bundle exec jekyll serve

# 4. Publish
git add .
git commit -m "New post: title of your post"
git push origin main
```

GitHub builds and publishes automatically in ~2 minutes.

---

## Key Files Reference

| File                      | Purpose                                  |
| ------------------------- | ---------------------------------------- |
| `_config.yml`             | Site-wide settings, name, social links   |
| `_pages/about.md`         | Home page / hero section                 |
| `_pages/cv.md`            | Experience and education                 |
| `_pages/talks.md`         | Speaking engagements with YouTube embeds |
| `_pages/mentoring.md`     | Community, mentoring, judging            |
| `_posts/`                 | Blog articles (one .md file per post)    |
| `assets/img/prof_pic.jpg` | Your profile photo                       |
| `_data/navigation.yml`    | Top navigation links                     |

---

## Troubleshooting

**`bundle install` fails:** Make sure Ruby Devkit was installed. Re-run the MSYS2 installer step from Phase 1.1.

**Site not updating after push:** Check the Actions tab in GitHub for build errors.

**`jekyll serve` port conflict:** Run `bundle exec jekyll serve --port 4001` instead.

**Images not showing:** Make sure file names match exactly (case-sensitive on GitHub).

---

## Profile Summary for Reference

- **Name:** Dipjyoti Das
- **Title:** Generative AI Architect
- **Location:** Charlotte, NC, USA
- **Experience:** 13+ years (2013–present)
- **Current employer:** Ascendion
- **Key clients:** Charter Communications, Fannie Mae, AT&T, CareSource, Duke Energy, Brighthouse Financial
- **Impact highlights:** $240M revenue (Brighthouse), 60% support call reduction (Charter), 70% faster valuations (Fannie Mae)
- **Speaking:** AIM 2026 SFO (Session Chair), Ai4 2021, RE.WORK AI
- **Mentoring:** Great Learning / UT Austin AIML Program (~20 professionals)
- **Judging:** Pinnacle Solutions Hackathon 2026, Technovation Girls (in progress), SWE India Scholarship
- **Memberships:** IEEE Senior Member, SWE (in progress)
- **GitHub:** https://github.com/dipjyotidas
- **LinkedIn:** https://www.linkedin.com/in/dipjyotidas/
