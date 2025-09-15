# Quick Reference Cheat Sheet — Terminal & Git (one page)

Essential commands and safety tips for students. Print or distribute as a one-page handout.

Terminal basics
- pwd — show current folder
- ls, ls -la — list files
- cd <path> — change directory
- mkdir -p <path> — make folders
- touch <file> — create empty file
- cat <file> — show file contents
- mv <src> <dst> — move/rename
- cp <src> <dst> — copy
- rm <file> — remove file (be careful)
- history — show recent commands
- ctrl+c — cancel current command

Git common
- git status — see changed files
- git add <file> — stage a file
- git commit -m "message" — save staged changes locally
- git log --oneline -n 5 — recent commits
- git branch — list branches
- git checkout -b feature/name — create & switch to a branch
- git checkout main — switch to main
- git merge feature/name — merge a branch into current
- git remote -v — show remote URLs
- git push -u origin <branch> — push branch to remote
- git pull --rebase origin main — update local branch safely

Safety & undo
- git stash save "wip" — save unfinished work temporarily
- git stash list
- git stash pop — restore last stash
- git revert <sha> — create a new commit that undoes <sha> (safe for shared branches)
- git reset --soft HEAD~1 — undo last commit but keep changes staged
- git reset --mixed HEAD~1 — undo last commit, keep changes in working tree
- git reset --hard HEAD~1 — DANGEROUS: discards working tree changes
- git reflog --oneline — find commits and recover lost work
- Always create a backup branch before risky commands: `git branch backup-before-reset`

SSH & GitHub
- ssh-keygen -t ed25519 -C "you@example.com" — create SSH key
- cat ~/.ssh/id_ed25519.pub — show public key
- eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_ed25519 — add key to agent
- Test: ssh -T git@github.com
- WSL copy tip: cat ~/.ssh/id_ed25519.pub | clip.exe

Quick workflow (recommended)
1) git checkout -b feature/short-description
2) make small change(s)
3) git add <files>
4) git commit -m "feat: short description"
5) git push -u origin feature/short-description
6) Open Pull Request, review, merge to main

Notes for teachers
- Prefer PR-based grading and branch protection on `main`.
- Teach `git status` and `git diff` before merge exercises.

