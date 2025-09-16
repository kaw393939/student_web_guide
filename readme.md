# Student Web Developer Guide — Cohort Workflow (2025)

A classroom-ready guide for phone-native beginners to learn the terminal, Git, Markdown, and realistic collaboration workflows while producing a student-authored site. The class ends with roughly 20 polished pages plus an index, with AI-generated illustrations used responsibly.

## ⚡️ At a glance
- What you’ll build: ~20 curated, student-written articles plus a simple index; optional AI images with alt text and credits.
- How you’ll work: small feature branches → PRs → peer/instructor review → squash merge to a protected `main`; recovery toolkit (stash/reset/revert/reflog) taught early.
- Start here:
	- Students: open [`modules/01-setup-first-article.md`](modules/01-setup-first-article.md) and copy [`templates/article.md`](templates/article.md) to `articles/m01-arpanet-<lastname>.md`.
	- Instructors: skim [`TEACHER_NOTES.md`](TEACHER_NOTES.md), enable branch protection on `main`, require PR reviews; see Deployment below for GitHub Pages.

Who this is for
- High school or intro college classes with mixed devices (macOS, Windows/WSL, Linux)
- Teachers who prefer PR-based grading and reproducible workflows

What you’ll build
- ~20 short, student-authored articles/checklists curated into a single site, plus an index
- Each page uses the standard article template and optional AI images with alt text and credits

Outcomes (skills)
- Terminal basics (pwd/ls/cd), working in a repo, and safe Git (branches, PRs, recovery)
- Markdown authoring with images and links; accessibility (alt text)
- Team workflows: forks, conflicts, reviews, and release/deploy basics

## Repository structure (current)
- [`modules/`](modules/) — Final 6-module plan (student track)
- [`templates/`](templates/) — article and index scaffolds
- [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) — PR template
- [`PR_CHECKLIST.md`](PR_CHECKLIST.md) — self-review checklist to paste into PRs
- [`TEACHER_NOTES.md`](TEACHER_NOTES.md) — troubleshooting and classroom guidance
- [`CHEAT_SHEET.md`](CHEAT_SHEET.md) — 1-page terminal/Git cheat sheet
- [`GIT_NINJA.md`](GIT_NINJA.md) — advanced Git (metaphor + recovery)
- [`GLOSSARY.md`](GLOSSARY.md) — terms and quick definitions
- [`reports/`](reports/) — [`team-report-template.md`](reports/team-report-template.md) (final team reflection)

Course modules (6)
- 01 — Setup, First Article, Git Basics: [`modules/01-setup-first-article.md`](modules/01-setup-first-article.md)
- 02 — Individual Feature Workflow: [`modules/02-individual-feature-workflow.md`](modules/02-individual-feature-workflow.md)
- 03 — Recovery Toolkit: [`modules/03-recovery-toolkit.md`](modules/03-recovery-toolkit.md)
- 04 — Solo PR Practice (Remote, Push, Review): [`modules/04-solo-pr-practice.md`](modules/04-solo-pr-practice.md)
- 05 — Team GitFlow (Forks, Conflicts, Integration): [`modules/05-team-gitflow-conflicts.md`](modules/05-team-gitflow-conflicts.md)
- 06 — Advanced Collaboration (Issues, Releases, Deploy): [`modules/06-advanced-collab-release.md`](modules/06-advanced-collab-release.md)

Target deliverables (~20 pages)
- Individual drafts (curated): 3–4 per student across early modules
- Team outputs: 3–4 polished articles per team, plus a global index and team reports
- With ≈5 teams, this yields ≈15–20 curated articles + the index

Image workflow (AI allowed, documented)
- Use the article front-matter fields: `image`, `image_alt`, `image_credit`
- Keep prompts/credits documented in the PR description or alongside images
- Prefer small files (< ~200 KB) and version filenames when iterating (e.g., `m02-browsers-v2.jpg`)

Article template (front-matter)
- See `templates/article.md` and copy it to your article path (examples below)

Example article paths
- Individual: `articles/m01-arpanet-smith.md`
- Team: `articles/team-2-browsers.md`

Branch & PR conventions
- Branch per article/feature, e.g. `feature/smith-m02-browsers`
- PR titles: `[Review] m02: browsers — Smith` (or `feat(m02): browsers — Smith`)
- Always include a short synopsis and sources in the PR description and paste the checklist from `PR_CHECKLIST.md`

Quickstart — students (first 10 minutes)
1) Open this repo in VS Code and the integrated terminal
2) Confirm Git: `git --version`
3) Create a feature branch for your first article
4) Copy `templates/article.md` to `articles/m01-arpanet-<lastname>.md` (see example in `templates/article-example.md`)
5) Commit and push; open a Draft PR; request 1 peer
 
Tip: If a term is unfamiliar, check the [`GLOSSARY.md`](GLOSSARY.md).

Recommended flow (high level)
- Research → write draft in Markdown → commit to a branch → open PR → peer suggestions → revise → merge
- Teams later fork the canonical repo, curate top drafts, add new team pages, and open PRs back to the canonical repo

Assessment & review (suggested)
- Use PRs for grading; require 1 peer approval + instructor sign-off
- Enforce front-matter completeness, working links, and alt text for any images
- Prefer squash merges to keep history tidy

Teacher setup (quick checklist)
- Protect `main` and require PR reviews before merge
- Use the PR template and `PR_CHECKLIST.md` for grading
- Form 3–4 person teams by Module 05 and assign roles (Author, Editor, Reviewer, Integrator)

Deployment (optional but encouraged)
- Enable GitHub Pages on the main (or docs) branch after the final integration
- Build an `index.md` using [`templates/index.md`](templates/index.md) and link all curated pages with one-line summaries

Troubleshooting & recovery
- Use `CHEAT_SHEET.md` for quick commands
- Use `GIT_NINJA.md` for advanced flows and the “Git as Video Editing” metaphor
- For safe undo: prefer `git revert` on shared branches; practice `stash/reset/reflog` on a backup branch first

Helpful background reading
- ARPANET background (student-friendly): [resources/arpanet-background.md](resources/arpanet-background.md)

Contributing rules (students)
- Keep changes focused per PR (one page/feature)
- Include sources at the end of each article under a “Sources” heading
- If you add images: include `image_alt` and `image_credit`; document your prompt briefly

For instructors
- Start with branch protection on `main`; require PRs
- Optionally create team forks in an org and accept PRs back into the canonical repo
- Use `reports/team-report-template.md` for final reflections

Attribution & classroom safety
- This repo is designed to be self-contained and classroom-safe; avoid pasting large copyrighted excerpts
- When in doubt, summarize in your own words and cite the source link

Next steps
- New learners: open `modules/01-setup-first-article.md` and start your first draft
- Instructors: scan `TEACHER_NOTES.md` and the templates folder, then set branch protection and review requirements
