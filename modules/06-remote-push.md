### Module 06 — Add Remote & Push (20–30 minutes)

Goal: create a remote repository on GitHub, connect it via SSH, and push your local main branch.

Estimated time: 20–30 minutes

Tasks

1) Create a new repository on GitHub (teacher can pre-create or students can create personal repos)

2) Connect remote and push

```bash
git remote add origin git@github.com:YOUR_USERNAME/what-we-wish-we-knew.git
git branch -M main
git push -u origin main
git remote -v
```

Deliverable: repo link + `git remote -v` output.

Teacher notes
- Discuss branch protection and single-user workflows. For classrooms, teacher may enable branch protection on `main` and require PRs.

---
