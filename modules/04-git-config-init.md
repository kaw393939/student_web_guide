### Module 04 — Git Config & Initialize Repo (20–30 minutes)

Goal: set up Git identity and initialize a local repository with an initial commit.

Estimated time: 20–30 minutes

Tasks

1) Configure Git identity

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global core.editor "code --wait"
git config --list
```

Deliverable: paste `git config --list` output (teacher verifies name/email set).

2) Initialize the local repo and make the first commit

```bash
cd ~/student-projects/what-we-wish-we-knew || cd ./
git init
git add .
git commit -m "chore: initial project files"
git log --oneline -n 3
```

Deliverable: `git log --oneline` shows the initial commit.

Teacher notes
- Explain atomic commits and why commit messages matter. Use conventional prefixes: `feat:`, `fix:`, `docs:`, `chore:`.

---
