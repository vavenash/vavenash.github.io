# vavenash.github.io

Personal portfolio and résumé site for **Avenash Vasant** — Platform Engineer, Cloud Architect, and Agentic AI builder.

Live at: **https://vavenash.github.io**

---

## What this site is

A single-page application (SPA) built with plain HTML/CSS and vanilla JavaScript — no build step, no framework, no dependencies beyond a Google Fonts stylesheet. It hosts:

| Tab | Contents |
|-----|----------|
| **Home** | Professional summary, work experience, key achievements, skills, certifications |
| **AI Projects** | Agentic AI projects built in 2026 (RAG pipelines, multi-agent systems, AgentOps CI/CD) |
| **Blog** | Short engineering write-ups on cloud platforms, SRE, and agentic AI |

---

## How the page is maintained

### Source of truth
`index.html` is the single source of truth. All content — résumé data, project cards, blog posts, and styles — lives in that one file. There are no templates, no CMS, and no build pipeline.

### Updating résumé content
Edit `index.html` directly. The main sections are clearly commented:

```
<!-- HOME -->        Professional summary, experience, certifications, skills
<!-- AI PROJECTS --> Agentic AI project cards
<!-- BLOG -->        Blog post articles
```

Keep a copy of your latest résumé `.docx` locally. When the résumé changes, update the matching sections in `index.html` by hand (or with AI assistance — see below).

### Adding a new AI project
Find the `<div class="project-grid">` block inside the `#projects` section and add a new `<div class="project-card">` entry following the existing pattern. Use `status-badge active` or `status-badge wip` to reflect the project's state.

### Adding a blog post
Add a new `<article class="post">` inside the `#blog` section's `.blog-col-8` column. Follow the existing article structure (heading, meta date/read-time, tags, excerpt, link).

### Styling
CSS lives in the `<style>` block in `<head>`. The design uses CSS custom properties (`--bg`, `--card`, `--text`, `--brand`, `--accent`) for both dark and light themes. Theme state is persisted to `localStorage`.

### AI-assisted maintenance
This page is maintained with Claude Code (Anthropic). To update content from a new résumé:

1. Upload your latest `.docx` to a Claude Code session with this repo open.
2. Prompt: *"Update index.html to reflect the latest résumé — update summary, experience bullets, certifications, and add any new projects."*
3. Review the diff, commit, and push.

### Deployment
GitHub Pages serves the repo root on every push to `main`. No CI pipeline is needed — just push and the live site updates within ~30 seconds.

```
git add index.html
git commit -m "update: <what changed>"
git push origin main
```

---

## File structure

```
vavenash.github.io/
├── index.html          # The entire site
├── assets/
│   ├── profile.jpg     # Avatar photo
│   └── favicon.svg     # Browser tab icon
└── README.md           # This file
```

---

## Print / PDF résumé

Click **Download PDF** on the site, or use the browser's **Print → Save as PDF** function. The print stylesheet hides navigation and CTA buttons so the output is clean.

---

## Local preview

No build step needed — just open `index.html` in a browser:

```bash
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

Or serve it locally to avoid any path issues:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```
