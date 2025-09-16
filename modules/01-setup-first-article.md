### Module 01 — Setup, First Article, Git Basics (45–60 min)

Goal: get a working environment, write the first short article using the template, and make a first branch/commit. Establish image workflow.

At a glance
- Deliverable: 1 article draft (`articles/m01-arpanet-<lastname>.md`) + optional image
- Skills: environment check, Markdown, branching, PR draft

Outputs (counts toward ~20 total):
- 1 individual article draft: `articles/m01-arpanet-<lastname>.md`
- Optional: 1 AI image `images/student-<lastname>/m01-arpanet-v1.(png|jpg)` + `images/student-<lastname>/prompts.md`

Steps
0) Prepare folders (first time only): create `articles/` and `images/student-<lastname>/` (2–3 min).
1) Environment check (macOS/WSL) and `git --version`, `pwd`, `ls -la` (10–15 min).
2) Read `resources/arpanet-background.md` (5–10 min).
3) Copy `templates/article.md` → `articles/m01-arpanet-<lastname>.md` and fill in front-matter (include `summary`) (15–20 min).
4) Create branch `feature/<lastname>-m01-arpanet`; commit your article (5–10 min).
5) If remote ready, push and open a DRAFT PR titled `[Draft] m01: ARPANET — <lastname>` (5 min).

Acceptance criteria
- Article uses template; front-matter (including `summary`) is complete; 300–400 words; 2–3 sources with links; alt text if image used.
- Branch exists and includes at least one commit with a clear message.

Image & credit rules
- Save AI prompts in `images/student-<lastname>/prompts.md`.
- Add `image:` and `image_credit:` to front-matter when including image(s).
- Keep images reasonably small (< ~200 KB when possible) and version filenames when iterating (e.g., `m01-arpanet-v2.jpg`).
 
Example: linking an image in Markdown
```
![Packet switching diagram](images/student-smith/m01-arpanet-v1.jpg)
```

Glossary
- New terms? See the course [`GLOSSARY.md`](../GLOSSARY.md) for quick definitions.
