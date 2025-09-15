### Module 07 — Branching & Feature Workflow (30–40 minutes)

Goal: use branches for safe experimentation and learn how to merge features back into `main`.

Estimated time: 30–40 minutes

Tasks

1) Create a feature branch

```bash
git checkout -b feature/first-article
```

2) Make changes and commit

```bash
# edit modules/your-name-intro.md
git add modules/your-name-intro.md
git commit -m "feat: add first article draft by <your-name>"
git push -u origin feature/first-article
```

3) Merge feature into main (local fast-forward or via PR on GitHub)

Local merge:

```bash
git checkout main
git merge --no-ff feature/first-article -m "chore: merge feature/first-article"
git push origin main
```

Deliverable: feature branch exists on remote and `main` contains the merged content.

Teacher notes
- For safety, demonstrate merging via GitHub Pull Request and showing how CI (if present) can help.

---
