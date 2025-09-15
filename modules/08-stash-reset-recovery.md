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

2) Undo last commit safely (soft vs mixed vs hard)

```bash
git log --oneline -n 5
git reset --soft HEAD~1   # keep changes staged
git reset --mixed HEAD~1  # keep changes in working tree
# git reset --hard HEAD~1 # DANGEROUS: discards changes
```

Teacher note: explain that `--hard` permanently discards uncommitted changes; always make a backup commit before using `--hard`.

3) Revert a commit (safe for shared branches)

```bash
git revert <commit-sha>
```

4) Recover lost commits with reflog

```bash
git reflog --oneline
# find a SHA that had your commit
git checkout -b recover-branch <sha>
# now push or inspect commit
```

Deliverable: demonstrate recovering a commit from reflog and creating a branch from it.

---
