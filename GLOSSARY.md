# Glossary — Student Web Developer Guide

This glossary explains key terms used across the course and gives a short "who, what, why, when, how" history for Git and Linux to help students understand the origins and purpose of the tools they use.

Table of contents
- Terms (A–Z)
- Git: who/what/why/when/how
- Linux: who/what/why/when/how

---

Terms (A–Z)

- API (Application Programming Interface)
  - What: A defined set of rules for how software components communicate.
  - Why: APIs let programs talk to each other and let developers reuse services.
  - Student tip: think of an API like a restaurant menu — you place an order and the kitchen (service) responds.

- Branch
  - What: A separate line of development in Git used to isolate work.
  - Why: Enables multiple people or experiments without changing the main production history.

- Commit
  - What: A recorded snapshot of staged changes in Git.
  - Why: Records progress and provides a point you can revert to or recover from.

- Clone
  - What: Making a local copy of a remote Git repository.

- Diff
  - What: Short for "difference" — shows what changed between two files or commits.

- Fork
  - What: A server-side copy of a repository (common on GitHub) used for independent development.

- Git
  - What: A distributed version control system for tracking changes to files.

- Merge
  - What: Integrating changes from one branch into another.

- Pull Request (PR)
  - What: A request to merge changes from one branch into another on a remote hosting platform; it enables code review.

- Push
  - What: Uploading local commits to a remote repository.

- Rebase
  - What: Rewriting commits to apply them on top of another base commit; used to create a linear history.

- Reflog
  - What: A local record of where the HEAD reference has been; useful for recovering lost commits.

- Repository (repo)
  - What: A folder tracked by Git that contains the project history.

- Shell / Terminal
  - What: Text-based interface to interact with your operating system.

- SSH (Secure Shell)
  - What: Protocol for secure remote access and authentication. Commonly used with Git hosts.

- Stash
  - What: A temporary storage area in Git for uncommitted changes.

- Tag
  - What: A named reference to a specific commit (often used for releases).

- WSL (Windows Subsystem for Linux)
  - What: A compatibility layer that allows running Linux distributions on Windows.

---

Git: who / what / why / when / how

- Who: Created by Linus Torvalds in 2005, with Junio Hamano later becoming the maintainer and principal developer who steered Git's evolution.
- What: A fast, distributed version control system built to handle large projects (originally the Linux kernel).
- Why: Created because existing VCS options of the time didn't meet the Linux kernel project's needs (performance, distributed workflows, strong integrity guarantees).
- When: Git was initially released in April 2005.
- How: Linus designed Git with a focus on content-addressable storage (SHA-1 historically), explicit object models (blobs, trees, commits), and cheap branching/merging operations.

Key points for students
- Git is distributed: every clone contains the full history, which enables offline work and local recovery.
- Branching is cheap: use branches for every change, experiment, and PR.
- Safety first: learn `reflog`, `revert`, and `stash` to recover from mistakes.

---

Linux: who / what / why / when / how

- Who: The Linux kernel was started by Linus Torvalds in 1991 as a personal project; many thousands of contributors have since contributed. The full operating systems called "Linux distributions" are built by many organizations and communities (Debian, Ubuntu, Red Hat, etc.).
- What: Linux is an open-source operating system kernel; combined with GNU tools and other software, it forms a complete OS commonly used on servers, desktops, and embedded devices.
- Why: Torvalds wanted a POSIX-compatible, free (as in freedom) kernel for x86 machines; the combination with GNU tools provided the rest of the userland.
- When: Kernel development began in 1991; the first versions were shared publicly in late 1991 and early 1992.
- How: The kernel manages hardware, processes, memory, and system calls. The ecosystem around Linux (distributions) packages the kernel with tools and package managers.

Key points for students
- The command-line culture comes from Unix and Linux history. Many of the tools you use (shells, editors, build tools) are inherited from decades of open-source development.
- Learning the shell is learning a core, transferable skill used across platforms.

---

Further reading
- Pro Git book: https://git-scm.com/book/en/v2
- Linux kernel history: https://www.kernel.org/
- GitHub documentation: https://docs.github.com


