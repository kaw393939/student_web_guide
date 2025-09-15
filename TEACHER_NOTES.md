# Troubleshooting & Teacher Notes

This consolidated reference collects common student problems, classroom tips, and safe recovery recipes. Use it during setup and troubleshooting.

1) Common environment issues

- Git missing (macOS / WSL)
  - macOS: install Homebrew then `brew install git`.
  - WSL (Ubuntu): `sudo apt update && sudo apt install git -y`.

- WSL not installed / misconfigured
  - Provide teacher-prepared images or a class VM if many students use Windows.
  - Prefer macOS or school-managed Linux machines if available.

- VS Code not installed or not in PATH
  - Point students to https://code.visualstudio.com/ and show "code ." usage after installation.

2) SSH & GitHub access

- Students can't copy-paste public key from WSL
  - Use `cat ~/.ssh/id_ed25519.pub | clip.exe` in WSL2 to copy to Windows clipboard.
  - Alternatively, open the file with `code ~/.ssh/id_ed25519.pub` and copy from VS Code.

- `ssh -T git@github.com` fails with permission denied
  - Confirm the public key was added to the correct GitHub account.
  - Check `~/.ssh/config` for interfering settings.
  - Run `ssh -vT git@github.com` for verbose debugging.

- Students share a single machine account
  - Require students to use separate GitHub accounts or submit files locally for teacher upload. Consider teacher-managed org repos.

3) Git basics and student confusion

- "Why didn't my file change show up on GitHub?"
  - Explain `git add` (stages) vs `git commit` (records) vs `git push` (uploads).
  - Show `git status` frequently.

- Accidental commits to `main`
  - If `main` is unprotected and they pushed, use `git revert <sha>` on the remote to undo safely.
  - Teach `git branch backup-before-merge` to create a local safety point before risky ops.

4) Dangerous commands & recovery

- `git reset --hard`
  - Always create a backup branch first: `git branch backup-before-reset`.
  - If they still lose work, use `git reflog` to find the lost commit and `git checkout -b recover-branch <sha>`.

- `git push --force` accidents
  - If a force-push overwrote history, you can often recover commits via reflog on a local clone that had the old history. Keep teacher copies of canonical repos.

5) Conflict resolution guidance

- Walk students through `git status`, `git diff`, and the conflict markers `<<<<<<<`.
- Let students practice in pairs: intentionally create a conflict and resolve it together.
- For rebases, explain `git rebase --continue` and `git rebase --abort`.

6) WSL-specific notes

- File permission and path quirks
  - Avoid editing Linux files from Windows tools that may change line endings or permissions. Use VS Code's Remote - WSL extension.
- Clipboard access
  - Use `clip.exe` or VS Code to move text between environments.

7) Classroom workflows & grading suggestions

- Prefer PR-based grading: students open a Pull Request from a feature branch and teacher reviews.
- For beginners, teacher can create private repos for each student and grant access.
- Keep exercises small and timeboxed (30-60 minutes each). Focus feedback on clarity and correctness, not polish.

8) Quick recovery recipes (handout)

- Recover last committed file (if not overwritten):
  - `git reflog --oneline` then `git checkout -b recover-branch <sha>`

- Recover staged but uncommitted changes (if you used reset):
  - `git fsck --lost-found` (advanced; teacher assist recommended)

9) Links & references

- Git basics: https://git-scm.com/docs
- GitHub SSH docs: https://docs.github.com/en/authentication/connecting-to-github-with-ssh
- VS Code Remote - WSL: https://code.visualstudio.com/docs/remote/wsl


Teacher: keep this file in the repo and open it during setup. Add school-specific instructions (e.g., VPN, proxy) as needed.
