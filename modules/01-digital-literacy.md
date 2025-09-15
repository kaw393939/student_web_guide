### Module 01 — Digital Literacy & Environment Setup (45–60 minutes)

Goal: ensure every student has a working development environment (macOS Terminal or WSL2 Ubuntu), understands basic file concepts, and completes a first Markdown writing exercise.

Estimated time: 45–60 minutes (can be split into two class periods)

Tasks

1) Welcome & short mindset (5 minutes)

- Quick note: you already use apps every day. This course builds on that experience and teaches you how to make things that other people can use.

2) Environment setup (20–35 minutes)

- macOS: open Terminal (Cmd+Space → Terminal) and run:

```bash
git --version
uname -a
```

- Windows (WSL2): if not installed, follow teacher's WSL2 install instructions (teacher may pre-install). Open Ubuntu terminal and run:

```bash
git --version
lsb_release -a
```

If `git` is missing, install it:

macOS (Homebrew):

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install git
```

Ubuntu (WSL):

```bash
sudo apt update
sudo apt install git -y
```

Deliverable: Paste `git --version` output and either `uname -a` or `lsb_release -a` into the class chat.

3) File concepts & first folder (10 minutes)

```bash
cd ~
mkdir -p student-projects/what-we-wish-we-knew
cd student-projects/what-we-wish-we-knew
pwd
ls -la
```

Explain: folders (directories) hold files. `pwd` shows current folder. `ls` lists files.

4) First Markdown writing (15–20 minutes)

- Create `modules/your-name-intro.md` with a short note (150–250 words) about why you want to learn web development.
- Use headings and one small bullet list.
- Save the file.

Example starter paragraph:

> I'm learning web development because I want to make things that help people. I use apps every day and I want to understand how they’re made. This course will help me write and publish my first web content.

5) (Optional now) Save your work with Git (10 minutes)

If you'd like to save your work with Git now, you can initialize a local repository. Otherwise we'll do this in Module 04 to keep initialization consistent across the class.

```bash
# only if you want to initialize now
git init
git add modules/your-name-intro.md
git commit -m "docs: add intro article by <your-name>"
git log --oneline -n 3
```

Deliverable: `modules/your-name-intro.md` present. If you initialized, a local commit is recorded.

Teacher notes
- Expect many students to need help with WSL installation and VS Code setup. Reserve class time for hands-on setup.
- If students cannot create accounts, they can work locally and hand in the `modules/your-name-intro.md` file.

Prompts students can copy into Copilot Chat
- "Please rewrite my paragraph in friendly, plain English for a high school student who uses phones. Keep it under 120 words."
- "Suggest 3 simple metaphors that explain what a file system is to someone who only uses apps."

---
