# 📝 Version Control with Git

## Table of Contents
- [What is Git and Why It Matters](#what-is-git-and-why-it-matters)
- [Installing Git](#installing-git)
- [Git Basics and Essential Commands](#git-basics-and-essential-commands)
- [Working with GitHub](#working-with-github)
- [Git Workflows and Best Practices](#git-workflows-and-best-practices)
- [Git Collaboration](#git-collaboration)
- [🎯 **Hands-On Assignment: Git Fundamentals**](git-assignment-1.md) ⭐

---

## What is Git and Why It Matters

Git is a **distributed version control system** that tracks changes in your code over time. Think of it as a time machine for your projects that allows you to:

- 📸 **Save snapshots** of your code at any point
- 🔄 **Revert changes** when something breaks
- 🤝 **Collaborate** with other developers
- 🌿 **Work on features** in parallel without conflicts
- 📊 **Track who changed what** and when

### Why Every Developer Needs Git

1. **Backup your work** - Never lose code again
2. **Experiment safely** - Try new features without fear
3. **Professional requirement** - Every company uses version control
4. **Portfolio building** - Showcase your projects on GitHub
5. **Learning from others** - Explore open-source projects

## Installing Git

### Mac Installation

Git comes with Xcode Command Line Tools, but let's get the latest version:

```bash
# Install latest Git via Homebrew
brew install git

# Verify installation
git --version
```

### WSL2 Installation

```bash
# Update package list
sudo apt update

# Install Git
sudo apt install git -y

# Verify installation
git --version
```

### Initial Git Configuration

**Set your identity** (required for all commits):

```bash
# Set your name (use your real name)
git config --global user.name "Your Full Name"

# Set your email (use the same email as your GitHub account)
git config --global user.email "your.email@example.com"

# Set default branch name to 'main'
git config --global init.defaultBranch main

# Make Git output more colorful
git config --global color.ui auto

# Set VS Code as default editor
git config --global core.editor "code --wait"
```

**Verify your configuration:**

```bash
git config --list --global
```

## Git Basics and Essential Commands

### Understanding Git Concepts

#### Repository (Repo)
A folder that Git is tracking. Contains your project files plus a hidden `.git` folder with all the version history.

#### Working Directory
The current state of your files that you can see and edit.

#### Staging Area (Index)
A temporary space where you prepare changes before committing them.

#### Commit
A snapshot of your code at a specific point in time, with a descriptive message.

### The Git Workflow

```
Working Directory → Staging Area → Repository
      ↓               ↓             ↓
   git add         git commit    git push
```

### Essential Git Commands

#### Starting a New Project

```bash
# Create a new directory and navigate into it
mkdir my-first-project
cd my-first-project

# Initialize a new Git repository
git init

# Check repository status
git status
```

#### Your First Commit

```bash
# Create a simple file
echo "# My First Project" > README.md

# Check what Git sees
git status

# Add file to staging area
git add README.md

# Check status again
git status

# Create your first commit
git commit -m "Initial commit: Add README"

# View commit history
git log
git log --oneline  # Shorter format
```

#### The Daily Git Workflow

```bash
# Check current status
git status

# Add specific files
git add filename.txt
git add folder/

# Add all changes (be careful!)
git add .

# Commit with descriptive message
git commit -m "Add user authentication feature"

# View changes before staging
git diff

# View staged changes
git diff --staged

# View commit history
git log
git log --graph --oneline --all  # Pretty graph view
```

#### Working with Branches

```bash
# List all branches
git branch

# Create and switch to new branch
git checkout -b feature-new-navbar

# Switch between branches
git checkout main
git checkout feature-new-navbar

# Merge branch into main
git checkout main
git merge feature-new-navbar

# Delete merged branch
git branch -d feature-new-navbar
```

### Git Best Practices

#### Commit Message Guidelines

**Good commit messages:**
```bash
git commit -m "Add user login validation"
git commit -m "Fix navbar responsive design issue"
git commit -m "Update README with installation instructions"
```

**Bad commit messages:**
```bash
git commit -m "stuff"
git commit -m "fixed bug"
git commit -m "updates"
```

#### Commit Frequency
- **Commit early and often** - Small, focused commits
- **One feature per commit** - Easy to understand and revert
- **Test before committing** - Don't commit broken code

#### File Management

Create a `.gitignore` file to exclude unwanted files:

```bash
# Create .gitignore file
touch .gitignore
```

Common `.gitignore` patterns:
```gitignore
# Dependencies
node_modules/
*.log

# Environment variables
.env
.env.local

# Build output
dist/
build/

# Editor files
.vscode/
.DS_Store

# Temporary files
*.tmp
*.swp
```

## Working with GitHub

### What is GitHub?

GitHub is a cloud-based hosting service for Git repositories. It provides:
- 🌐 **Remote storage** for your repositories
- 🤝 **Collaboration tools** for teams
- 📋 **Project management** features
- 🚀 **Free hosting** for static websites
- 💼 **Professional portfolio** platform

### Setting up GitHub

1. **Create account** at [github.com](https://github.com)
2. **Verify your email** address
3. **Set up SSH keys** (recommended) or use HTTPS

#### Setting up SSH Keys (Recommended)

**Generate SSH key:**
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

**Add to SSH agent:**
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

**Copy public key:**
```bash
# Mac
cat ~/.ssh/id_ed25519.pub | pbcopy

# WSL2
cat ~/.ssh/id_ed25519.pub
```

**Add to GitHub:**
1. Go to GitHub Settings → SSH and GPG keys
2. Click "New SSH key"
3. Paste your public key

**Test connection:**
```bash
ssh -T git@github.com
```

### Connecting Local Repository to GitHub

#### Method 1: Start Local, Push to GitHub

```bash
# In your existing local repository
git remote add origin git@github.com:yourusername/your-repo-name.git

# Push your code to GitHub
git push -u origin main
```

#### Method 2: Clone from GitHub

```bash
# Clone existing repository
git clone git@github.com:username/repository-name.git

# Navigate into cloned directory
cd repository-name
```

### Essential GitHub Workflow

```bash
# Daily workflow
git pull origin main        # Get latest changes
git checkout -b new-feature # Create feature branch
# ... make changes ...
git add .
git commit -m "Add new feature"
git push origin new-feature # Push to GitHub

# Create Pull Request on GitHub website
# After approval and merge:
git checkout main
git pull origin main        # Get updated main branch
git branch -d new-feature  # Delete local branch
```

## Git Workflows and Best Practices

### GitHub Flow (Recommended for Beginners)

This is a simple, GitHub-centered workflow perfect for students and small teams:

```
main branch (always deployable)
     ↓
feature branch (work on new features)
     ↓
Pull Request (code review and discussion)
     ↓
Merge to main (deploy)
```

#### Step-by-Step GitHub Flow

1. **Always start from updated main:**
```bash
git checkout main
git pull origin main
```

2. **Create descriptive branch:**
```bash
git checkout -b add-contact-form
```

3. **Make focused commits:**
```bash
git add contact.html
git commit -m "Add contact form HTML structure"

git add styles.css
git commit -m "Style contact form with CSS Grid"
```

4. **Push branch to GitHub:**
```bash
git push origin add-contact-form
```

5. **Create Pull Request on GitHub**
6. **Review, discuss, and merge**
7. **Clean up:**
```bash
git checkout main
git pull origin main
git branch -d add-contact-form
```

### Branch Naming Conventions

**Good branch names:**
- `feature/user-authentication`
- `fix/navbar-mobile-bug`
- `docs/update-readme`
- `refactor/cleanup-css`

**Bad branch names:**
- `john-branch`
- `stuff`
- `temp`
- `new`

### Handling Common Situations

#### Fixing Mistakes

**Undo last commit (keep changes):**
```bash
git reset --soft HEAD~1
```

**Undo changes to specific file:**
```bash
git checkout -- filename.txt
```

**Undo all unstaged changes:**
```bash
git restore .
```

#### Staying Up to Date

**Update your branch with latest main:**
```bash
git checkout main
git pull origin main
git checkout your-feature-branch
git merge main
```

## Git Collaboration

### Working on Team Projects

#### Forking Workflow (Open Source)

1. **Fork** repository on GitHub
2. **Clone** your fork locally
3. **Add upstream** remote:
```bash
git remote add upstream git@github.com:original-owner/repo.git
```

4. **Keep fork updated:**
```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

#### Pull Request Best Practices

**Before creating PR:**
- ✅ Test your code thoroughly
- ✅ Update documentation if needed
- ✅ Follow project coding standards
- ✅ Write clear commit messages

**PR Description should include:**
- What changes were made
- Why the changes were needed
- How to test the changes
- Screenshots (for UI changes)

### Resolving Merge Conflicts

When Git can't automatically merge changes:

1. **Git will mark conflicts in files:**
```html
<<<<<<< HEAD
<h1>Welcome to Our Site</h1>
=======
<h1>Welcome to My Website</h1>
>>>>>>> feature-branch
```

2. **Manually resolve conflicts:**
```html
<h1>Welcome to Our Website</h1>
```

3. **Mark as resolved:**
```bash
git add conflicted-file.html
git commit -m "Resolve merge conflict in header"
```

### Git Commands Cheat Sheet

| Command | Description |
|---------|-------------|
| `git status` | Check repository status |
| `git add .` | Stage all changes |
| `git commit -m "message"` | Create commit |
| `git push` | Upload to remote |
| `git pull` | Download from remote |
| `git checkout -b branch` | Create and switch branch |
| `git merge branch` | Merge branch into current |
| `git log --oneline` | View commit history |
| `git diff` | Show unstaged changes |
| `git reset HEAD~1` | Undo last commit |

---

## 🎯 **HANDS-ON ASSIGNMENT: Master Git Fundamentals**

### **[📋 Git Assignment 1: Complete Tutorial](git-assignment-1.md)**

**Ready to put your Git knowledge into practice?** Complete our comprehensive hands-on assignment that covers:

- ✅ **Repository Management** - Creating and managing Git repositories
- ✅ **Commit Mastery** - Making meaningful commits and managing history
- ✅ **Reset & Restore** - Undoing changes with soft/hard reset and restore
- ✅ **Branching & Merging** - Working with branches and resolving conflicts
- ✅ **Advanced History** - Exploring Git logs, blame, and grep

**🕒 Time Required:** 2-3 hours  
**📈 Difficulty:** Beginner to Intermediate  

**👉 [Start Assignment Now →](git-assignment-1.md)**

This assignment includes:
- Step-by-step instructions for every command
- Real-world scenarios and problem-solving
- Knowledge check questions throughout
- Challenge exercises to test your skills
- Complete deliverables and submission guide

---

## 🎯 Quick Practice Exercises

### Exercise 1: Create Your First Repository
1. Create a new folder for a project
2. Initialize Git repository
3. Create a simple HTML file
4. Make your first commit
5. Connect to GitHub and push

### Exercise 2: Practice Branching
1. Create a new branch for adding CSS
2. Add a stylesheet to your project
3. Commit the changes
4. Switch back to main and merge

### Exercise 3: Simulate Collaboration
1. Fork a repository on GitHub
2. Clone your fork locally
3. Make improvements
4. Create a Pull Request

---

*🎉 Congratulations! You now have a solid foundation in Git and GitHub. These skills will serve you throughout your entire development career.*

*📝 **Your Next Task:** Create your first repository on GitHub with a simple HTML page, practice the GitHub Flow by making changes on a feature branch, and create your first Pull Request!*

---

[← Back to Main Guide](readme.md) | [Next: Development Environment Setup →](development-setup.md)