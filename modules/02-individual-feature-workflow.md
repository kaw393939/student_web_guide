### Module 02 — Individual Feature Workflow (30–45 min)

Goal: practice a clean feature-branch → PR loop and write a short article on browsers/standards or similar topic.

At a glance
- Deliverable: 1 individual article (`articles/m02-<topic>-<lastname>.md`) + optional image
- Skills: feature branch, PR, peer review, revise

Outputs (counts toward ~20 total)
- 1 individual article: `articles/m02-<topic>-<lastname>.md` (e.g., browsers, HTML/CSS history, mobile OS)
- Optional: 1 AI image `images/student-<lastname>/m02-<topic>-v1.jpg` (+ record prompt in `images/student-<lastname>/prompts.md`)

Steps
1) Create a branch `feature/<lastname>-m02-<topic>` (5 min).
2) Draft your article using `templates/article.md` and save to `articles/m02-<topic>-<lastname>.md` (300–400 words) (20–25 min). Fill front-matter, including a 20–30 word `summary`.
3) Push branch and open a PR titled `[Review] m02: <short-title> — <lastname>` (5 min). Paste the self-review from `PR_CHECKLIST.md`.
4) Peer review: comment 3 concrete suggestions on a classmate’s PR; incorporate one suggestion into your article (10–15 min).

Front matter (what and why)
- Front matter is the small YAML block at the very top of your Markdown file (between `---` lines). It stores metadata that people and tools can read.
- We use it to build the class index and to check quality automatically (e.g., ensuring images have alt text and credits).

Example (copy and adapt)
```yaml
---
title: "Why Browsers Standardize the Web"
author: "<Your Name>"
date: 2025-09-15
summary: "20–30 words explaining your article in plain language; this goes into the site index and helps reviewers scan quickly."
image: images/student-<lastname>/m02-<topic>-v1.jpg      # optional
image_alt: "Short alt text for screen readers"          # required if image used
image_credit: "AI image — prompt: '<brief prompt>'"     # required if image used
---
```

Programmatic uses (how it helps you)
- Index: `title`, `author`, and `summary` are used to generate the final `index.md`.
- QA: If `image` is present, we expect `image_alt` and `image_credit` for accessibility and transparency.
- Sorting: `date` lets tools sort newest-first or group by week.

Acceptance criteria
- Front-matter complete (including `summary`); links verified; image credit + alt text if image used.
- Branch + PR created; at least one revision commit after peer feedback.

Success criteria (scan)
- 300–400 words, clear intro, 2+ sources
- Front-matter fields filled (`title`, `author`, `date`, `summary`, optional `image_*`)
- PR has checklist pasted; at least one revision commit
