### Module 09 — Collaboration: Pulls, Merges & Conflicts (30–45 minutes)

Goal: learn how to fetch/pull from remotes, handle merges, and resolve simple conflicts.

Estimated time: 30–45 minutes

Tasks

1) Fetch and pull

```bash
git fetch origin
git pull origin main
```

2) Create a conflict (simulated)

```bash
# Student A: on main, edit modules/your-name-intro.md and commit+push
# Student B: locally edit same lines, commit on feature branch, then merge/rebase
```

3) Resolve conflict

```bash
# when merge reports conflict, open file and look for <<<<<<< markers
# edit to decide final content
git add <file-with-conflict>
git commit -m "fix: resolve merge conflict in <file>"
git push
```

Deliverable: successfully resolve merge conflict and push merged result.

Teacher notes
- Use pair programming for conflict exercise: two students intentionally create the conflict and resolve together.
- Teach `git status` and `git diff` as primary debugging tools.

---
