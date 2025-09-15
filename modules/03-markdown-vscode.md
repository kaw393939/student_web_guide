### Module 03 — Markdown & VS Code (30–45 minutes)

Goal: write and preview Markdown in VS Code and learn basic project editing workflows.

Estimated time: 30–45 minutes

Tasks

1) Open the project in VS Code (5 minutes)

- Launch VS Code and open the project folder (File → Open Folder).
- Open the integrated terminal (View → Terminal).

2) Create your first Markdown article (15–25 minutes)

```bash
# if you created the student-projects folder in Module 01
cd ~/student-projects/what-we-wish-we-knew
# OR from the repo root
cd path/to/this/repository
code .
```

Open the project folder in VS Code. If you created `student-projects/what-we-wish-we-knew` in Module 01 use that path; otherwise open the repository root.

From the terminal you can run (optional):

```bash
# go to your project folder
cd ~/student-projects/what-we-wish-we-knew
# OR from the repo root
cd path/to/this/repository
# open VS Code from the current folder (optional; only if you have VS Code installed)
code .
```

- Create a file `your-name-intro.md` in the `modules/` folder.
- Write 150–250 words about why you want to learn web development. Use headings and one bulleted list.
- Use VS Code's Markdown preview (Ctrl+Shift+V or View → Preview) to see the rendered article.

Deliverable: `your-name-intro.md` saved in `modules/` with 150–250 words.

3) Basic Git steps (10–15 minutes)

```bash
git status
git add modules/your-name-intro.md
git commit -m "docs: add intro article by <your-name>"
git log --oneline -n 3
```

Deliverable: confirmation that commit exists (`git log --oneline`).

Teacher notes
- Encourage clear commit messages (what changed + why).
- If students are using the same machine accounts, instruct them to set `git config --global user.name` and `user.email`.

Prompts students can copy into Copilot Chat
- "Rewrite this paragraph in friendly, plain English for a high school student who uses phones."
- "Suggest three small examples to make this intro more interesting."

---
