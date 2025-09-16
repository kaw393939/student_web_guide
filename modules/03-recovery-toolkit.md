### Module 03 — Recovery Toolkit: Stash, Reset, Revert, Reflog (40–50 min)

Goal: learn safe undo techniques before team work.

Outputs (counts toward ~20 total)
- 1 short checklist article: `articles/m03-git-recovery-<lastname>.md` documenting what each command does and when to use it. Optional image allowed if it clarifies concepts.

Steps
1) Create a sandbox branch `lab/<lastname>-m03-recovery`.
2) Practice:
   - `git stash save "wip: edits"` → `git stash pop`
   - `git reset --soft HEAD~1` (with a backup branch first)
   - `git revert <sha>` to undo while preserving history
   - `git reflog` to find a lost commit and recover to `recovery/<sha-short>`
3) Write your checklist article with code blocks and warnings.

Acceptance criteria
- Article includes examples for each command and a safety checklist.
- Demonstrated recovery steps live or via screenshots/commands pasted in PR; PR uses `PR_CHECKLIST.md`.
