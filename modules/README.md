# Modules 3 (Final 6-Module Plan)

This folder contains the streamlined 6-module path that simulates a realistic developer workflow. It reuses ideas from `modules/` and `modules2/`, but each module here is re-scoped with clear outputs so the class ends with ~20 polished articles plus an index, with AI-generated images where appropriate.

- Module 01 — Setup, First Article, Git Basics
- Module 02 — Individual Feature Workflow (Branches, PRs)
- Module 03 — Recovery Toolkit (Stash/Reset/Revert/Reflog)
- Module 04 — Solo PR Practice (Remote, Push, Review)
- Module 05 — Team GitFlow (Forks, Conflicts, Integration)
- Module 06 — Advanced Collaboration (Issues, Releases, Deploy)

Use the templates in `templates/` for articles and the site index. Image prompts and credits should be saved alongside images.

Outcome tally toward ~20 artifacts
- Individual outputs: M01 (1), M02 (1), M03 (1 checklist), M04 (1) → up to 4 per student (teachers will curate).
- Team outputs: M05 (≈3–4 per team), M06 (index + team report). With 5 teams, that’s ≈15–20 curated articles plus the index.

Image pipeline rules
- Store student images under `images/student-<lastname>/` and team images under `images/team-<n>/`.
- Keep prompts in `images/.../prompts.md`; include `image` and `image_credit` in article front-matter; add alt text.
- Prefer small files (< ~200 KB) and version names like `m02-topic-v2.jpg` when iterating.

Helpful references
- Article scaffold: `templates/article.md`
- Index scaffold: `templates/index.md`
- PR checklist: `PR_CHECKLIST.md`
