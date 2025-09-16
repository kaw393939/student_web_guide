# GIT NINJA — Advanced use cases, productivity tips & recovery recipes

This cheat sheet collects practical, instructor-approved Git techniques and workflows for students ready to level up. It covers use-cases, commands, safety warnings, and one-line productivity accelerators. Use this after you've mastered the basics (Modules 1–4).

Table of contents
- Quick safety rules
- Productivity shortcuts
- Branching workflows
- Work-in-progress & stashing
- Rewriting history (rebases, fixups)
- Collaboration & review (PRs)
- Conflict resolution patterns
- Recovery recipes (reflog, reset, restore)
- Hooks, aliases, and config tips
- Advanced references

- Git as Video Editing (metaphor & classroom activity)

---

Git as Video Editing (metaphor & classroom activity)

This metaphor helps students understand commits and branching by comparing Git to editing a movie timeline.

Mapping (Git ↔ Video editing)
- Commit = Frame or saved edit point (a snapshot in time)
- git log = Timeline / edit history (scrub through frames)
- Branch = Alternate cut / version (director's cut vs classroom cut)
- Merge = Composite / final edit (combine cuts)
- Rebase = Re-timing / re-sequencing frames (move your edits on top of a new base)
- Stash = Temporary layer or clipboard (hide unfinished edits)
- Revert = Non-destructive undo (a new frame that negates an earlier change)
- Reset (soft/mixed/hard) = Destructive timeline edits (throwing away frames)
- Reflog = Playhead history / undo list (where the playhead has been)
- Push = Upload the rendered cut to the studio/server

Teacher script (copyable)
> "Think of your project as a movie. Every time you commit you save a frame. You can scrub these frames, create alternate cuts on branches, and merge the best parts into the final edit. If something looks wrong, you can rewind or make a backup branch before trying risky changes."

One-minute classroom activity (drop-in for Module 07 or 08)
1. Two students edit the same paragraph in a shared file, each on their own branch (`feature/A`, `feature/B`) and commit their changes.
2. Show `git log --oneline --graph` to visualize the timeline.
3. Merge `feature/A` into `main` locally, then merge `feature/B` to produce a conflict. Resolve the conflict together — explain this as combining two cuts.
4. Demonstrate `git reflog` recovery on a teacher-prepared disposable repo: do a `git reset --hard` and then recover the lost commit using reflog to show the rescue workflow.

README blurb (one line)
> "Think of Git like video editing for text: commits are frames on your project timeline, branches are alternate cuts, and merging is composing the final edit."


Quick safety rules
- Always create a backup branch before risky operations:

```bash
git branch backup-before-risk
```

- Prefer `git revert` for public/shared branches; prefer `git reset`/rebase only on local/private branches.
- Read commands before running them. If unsure, copy to a gist and ask a teacher.

---

Productivity shortcuts
- Show concise log with graph:

```bash
git log --oneline --graph --decorate --all --color
```

- One-line add-and-commit:

```bash
git commit -am "fix: message"
```

- Amend last commit (change message or add staged changes):

```bash
# amend with new staged changes
git add file
git commit --amend --no-edit
# or amend message interactively
git commit --amend -m "new message"
```

- Create a branch and switch in one step:

```bash
git switch -c feature/short-name
# or older git
git checkout -b feature/short-name
```

- Stage parts of a file interactively:

```bash
git add -p path/to/file
```

- Quick status with branch and remote info:

```bash
git status -sb
```

---

Branching workflows
- Feature branch workflow (local -> remote -> PR -> merge):

```bash
git switch -c feature/thing
# work, then
git add .
git commit -m "feat: add thing"
git push -u origin feature/thing
# open PR on GitHub and request review
```

- Keep main clean with protected branches and PRs.
- Use descriptive branch names: `feature/`, `fix/`, `chore/`, `docs/`.

---

Work-in-progress & stashing
- Save WIP when you need to switch branches:

```bash
git stash push -m "wip: partial intro"
# list stashes
git stash list
# apply and drop stash
git stash pop
# or apply without dropping
git stash apply stash@{1}
```

- Stash untracked files too:

```bash
git stash push -u -m "wip with untracked"
```

---

Rewriting history (rebases, fixups)
- Interactive rebase to clean up a series of commits:

```bash
# rewrite last 5 commits interactively
git rebase -i HEAD~5
```

- Use `--autosquash` with `fixup!` or `squash!` commits:

```bash
# make a fixup commit
git commit --fixup <sha>
# then
git rebase -i --autosquash <base-sha>
```

- Rebase workflow to update a feature branch on top of main:

```bash
git fetch origin
git switch feature/thing
git rebase origin/main
# resolve conflicts, then
git push --force-with-lease
```

Warning: don't force-push to shared branches without team agreement.

---

Collaboration & review (PRs)
- Push and open PR, request reviewers. Use Draft PRs if not ready.
- Use `git fetch` and `git pull --rebase` to keep local branches up-to-date before pushing.

---

Conflict resolution patterns
- Rebase conflict resolution flow:

```bash
# during rebase
# edit files to resolve conflicts
git add <resolved-files>
git rebase --continue
# if you want to stop and return to original
git rebase --abort
```

- Merge conflict resolution flow:

```bash
# during merge
# edit files to resolve
git add <resolved-files>
git commit -m "fix: resolve merge conflict"
```

Tips:
- Use `git status` and `git diff` frequently.
- Create a backup branch before attempting complex merges.

---

Recovery recipes (reflog, reset, restore)
- Find lost commits with reflog:

```bash
git reflog --oneline
# then restore
git checkout -b recover-branch <sha>
```

- Restore a deleted file from history:

```bash
# find the commit that had the file
git log -- path/to/file
# restore it
git checkout <commit-sha> -- path/to/file
```

- Convert a bad local repo to a fresh clone while preserving unpushed commits:

```bash
# list local branches and commits, note SHAs
git remote -v
# create a patch of unpushed commits
git format-patch origin/main..HEAD
# clone fresh
cd ..
git clone git@github.com:USER/REPO.git new-repo
# apply patches
cd new-repo
git am ../old-repo/*.patch
```

---

Hooks, aliases, and config tips
- Useful aliases to add in `~/.gitconfig`:

```ini
[alias]
  st = status -sb
  lg = log --oneline --graph --decorate --all
  co = checkout
  br = branch
  amend = commit --amend --no-edit
```

- Helpful config for consistent commits:

```bash
git config --global core.editor "code --wait"
git config --global init.defaultBranch main
```

- Client-side hooks example: `pre-commit` to run linters (useful later)

---

Advanced references
- Pro Git book: https://git-scm.com/book/en/v2
- Git reference: https://git-scm.com/docs
- GitHub help: https://docs.github.com

---

Teacher notes & safety
- Emphasize `--force-with-lease` over `--force` if rebasing and pushing to a branch you control.
- Teach `reflog` early as an escape hatch.
- Keep the cheat sheet in the repo for students to reference during labs.

