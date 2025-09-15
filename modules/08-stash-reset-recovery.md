### Module 08 — Stash, Reset, Revert & Recovery (40 minutes)

Goal: learn how to manage unfinished work, undo commits safely, and recover lost commits using `reflog`.

Estimated time: 40 minutes

Tasks

1) Stash unfinished changes

```bash
# make an edit to modules/your-name-intro.md but don't commit
git status
git stash save "wip: intro edits"
git stash list
git stash pop
```

Deliverable: stash list shows saved stash and `git stash pop` restores changes.

git log --oneline -n 5
git reset --soft HEAD~1   # keep changes staged
git reset --mixed HEAD~1  # keep changes in working tree
2) Undo last commit safely (soft vs mixed vs hard)

Always make a backup branch before running destructive commands:

```bash
git branch backup-before-reset
```

```bash
git log --oneline -n 5
git reset --soft HEAD~1   # keep changes staged
git reset --mixed HEAD~1  # keep changes in working tree
# git reset --hard HEAD~1 # DANGEROUS: discards working tree changes
```

Teacher note: explain that `--hard` discards local changes. Use `backup-before-reset` to recover if needed.

3) Revert a commit (safe for shared branches)

```bash
git revert <commit-sha>
```

git reflog --oneline
git checkout -b recover-branch <sha>
4) Recover lost commits with reflog

```bash
git reflog --oneline
# find a SHA that contained the commit you need
git checkout -b recover-branch <sha>
# inspect the commit, then push if desired
git log --oneline -n 5
```

Deliverable: demonstrate recovering a commit from reflog and creating a branch from it.

---
