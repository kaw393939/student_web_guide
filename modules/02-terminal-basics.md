### Module 02 — Terminal Basics (30–45 minutes)

Goal: get comfortable moving around the filesystem, creating and viewing files, and using the terminal safely.

Estimated time: 30–45 minutes

Tasks

1) Confirm environment (5 minutes)

```bash
git --version
uname -a   # macOS: shows kernel/version
lsb_release -a   # WSL/Ubuntu: shows distro info
```

Deliverable: copy-paste `git --version` and `uname -a` (or `lsb_release -a`) into class chat.

2) Basic navigation & listing (10 minutes)

Commands to try:

```bash
pwd
ls
ls -la
cd ~
mkdir -p ~/student-projects/what-we-wish-we-knew
cd ~/student-projects/what-we-wish-we-knew
```

Deliverable: create the `what-we-wish-we-knew` folder and show `ls -la` output.

3) Create and view files (10 minutes)

```bash
echo "Hello from <your-name>" > hello.txt
cat hello.txt
touch notes.md
```

Deliverable: `cat hello.txt` output and `ls -la` showing `hello.txt` and `notes.md`.

4) File operations (move/copy/remove) (10 minutes)

```bash
mkdir drafts
mv notes.md drafts/
cp hello.txt drafts/hello-copy.txt
rm drafts/hello-copy.txt
```

Deliverable: `ls drafts` shows `notes.md` and `mv` worked. Explain what `rm` did.

Teacher notes
- Encourage students to type commands manually; avoid copy-pasting everything until they understand it.
- Safety tip: show them `history` to see what they've run and `ctrl+c` to cancel running commands.

---
