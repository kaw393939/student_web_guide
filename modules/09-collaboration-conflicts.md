### Module 09 — Collaboration: Pulls, Merges & Conflicts (30–45 minutes)

Goal: learn how to fetch/pull from remotes, handle merges, and resolve simple conflicts.

Estimated time: 30–45 minutes

Tasks

1) Fetch and pull (safer with rebase)

```bash
git fetch origin
# prefer rebasing local changes on top of remote to keep history linear
git pull --rebase origin main
```

2) Create a conflict (simulated)

```bash
# Student A: on main, edit modules/your-name-intro.md and commit+push
# Student B: locally edit same lines, commit on feature branch, then merge/rebase
```

3) Resolve conflict

git commit -m "fix: resolve merge conflict in <file>"
git rebase --continue
git push
```bash
# when merge/rebase reports conflict, open the file and look for <<<<<<< markers
# edit to decide final content, remove the markers, then:
git add <file-with-conflict>
# if you were merging, finish the merge with a commit
git commit -m "fix: resolve merge conflict in <file>"
# if you used rebase, continue the rebase
git rebase --continue
git push

# If the rebase is confusing or you want to cancel, run:
git rebase --abort

# Safety tip: create a backup branch before risky operations
git branch backup-before-merge
```

Quick tips:
- Run `git status` and `git diff` to inspect conflicts.  
- If you're unsure, create a backup branch first: `git branch backup-before-merge`.

Deliverable: successfully resolve merge conflict and push merged result.

Teacher notes
- Use pair programming for conflict exercise: two students intentionally create the conflict and resolve together.
- Teach `git status` and `git diff` as primary debugging tools.

---
