# 🎯 Git Assignment 1: Mastering Fundamental Git Commands

## Assignment Overview

This hands-on assignment will teach you the essential Git commands that every developer must know. You'll learn to manage commits, undo changes, restore files, and handle merges through practical exercises.

**Estimated Time:** 2-3 hours  
**Difficulty:** Beginner to Intermediate  
**Prerequisites:** Git installed and configured

---

## 🎯 Learning Objectives

By completing this assignment, you will be able to:

- ✅ Create and manage Git repositories
- ✅ Make meaningful commits with proper messages
- ✅ Undo commits using soft and hard resets
- ✅ Restore files and directories
- ✅ Work with branches and merging
- ✅ Handle merge conflicts
- ✅ Use Git's history and logging features

---

## 📋 Assignment Tasks

### Task 1: Repository Setup and Basic Commits

#### Step 1: Create Your Assignment Repository

```bash
# Create a new directory for this assignment
mkdir git-assignment-practice
cd git-assignment-practice

# Initialize a new Git repository
git init

# Verify Git status
git status
```

#### Step 2: Create Your First Files and Commits

```bash
# Create a README file
echo "# Git Assignment Practice Repository" > README.md

# Create a simple HTML file
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice</title>
</head>
<body>
    <h1>Welcome to Git Practice</h1>
    <p>This is my first commit.</p>
</body>
</html>
EOF

# Check the status
git status

# Stage the files
git add README.md
git add index.html

# Make your first commit
git commit -m "Initial commit: Add README and basic HTML file"

# View the commit history
git log --oneline
```

#### Step 3: Practice Multiple Commits

```bash
# Add CSS styling
cat > styles.css << 'EOF'
body {
    font-family: Arial, sans-serif;
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f0f0f0;
}

h1 {
    color: #333;
    text-align: center;
}

p {
    line-height: 1.6;
    color: #666;
}
EOF

# Update the HTML to include CSS
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Welcome to Git Practice</h1>
    <p>This is my first commit.</p>
    <p>Now I'm learning about multiple commits!</p>
</body>
</html>
EOF

# Stage and commit the changes
git add .
git commit -m "Add CSS styling and update HTML content"

# Create a JavaScript file
cat > script.js << 'EOF'
console.log('Git assignment is working!');

document.addEventListener('DOMContentLoaded', function() {
    const h1 = document.querySelector('h1');
    h1.style.animation = 'fadeIn 2s ease-in';
    
    // Add some interactivity
    h1.addEventListener('click', function() {
        alert('You clicked the title!');
    });
});
EOF

# Update HTML to include JavaScript
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Welcome to Git Practice</h1>
    <p>This is my first commit.</p>
    <p>Now I'm learning about multiple commits!</p>
    <p>Click the title for a surprise!</p>
    
    <script src="script.js"></script>
</body>
</html>
EOF

# Add animation to CSS
cat >> styles.css << 'EOF'

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

h1:hover {
    cursor: pointer;
    color: #007acc;
}
EOF

# Commit these changes
git add .
git commit -m "Add JavaScript interactivity and CSS animations"

# View your commit history
git log --oneline --graph
```

**📝 Question 1:** How many commits do you have now? What does `git log --oneline` show you?

---

### Task 2: Understanding Git Reset (Soft vs Hard)

#### Step 4: Practice Soft Reset

```bash
# First, let's see our current state
git log --oneline

# Create a new file we'll use for testing
echo "This is a test file for reset practice" > test-file.txt
git add test-file.txt
git commit -m "Add test file for reset practice"

# Now let's make another commit
echo "Additional content" >> test-file.txt
git add test-file.txt
git commit -m "Update test file with additional content"

# Check the log again
git log --oneline

# Perform a SOFT reset (removes commit but keeps changes staged)
git reset --soft HEAD~1

# Check status and see what happened
git status
git log --oneline

# The changes are still staged! Let's commit them again
git commit -m "Re-add the additional content after soft reset"
```

#### Step 5: Practice Hard Reset

```bash
# Create another test scenario
echo "This will be removed by hard reset" > will-be-removed.txt
git add will-be-removed.txt
git commit -m "Add file that will be removed by hard reset"

# Make another commit
echo "More content to remove" >> will-be-removed.txt
git add will-be-removed.txt
git commit -m "Update file before hard reset"

# Check our log
git log --oneline

# Perform a HARD reset (removes commit AND discards changes)
git reset --hard HEAD~2

# Check status and log
git status
git log --oneline

# Notice: The file is completely gone!
ls -la
```

**📝 Question 2:** What's the difference between `git reset --soft` and `git reset --hard`? When would you use each?

---

### Task 3: Working with Git Restore

#### Step 6: Restore Staged Changes

```bash
# Create a new file and modify an existing one
echo "New feature file" > feature.txt
echo "Updated content in README" >> README.md

# Stage the changes
git add .

# Check what's staged
git status

# Now restore (unstage) just one file
git restore --staged feature.txt

# Check status again
git status

# The feature.txt is unstaged, but README.md is still staged
```

#### Step 7: Restore Working Directory Changes

```bash
# Make some changes to files without staging
echo "Unwanted changes" >> index.html
echo "More unwanted changes" >> styles.css

# Check the status
git status

# See the differences
git diff

# Restore the changes (discard them)
git restore index.html
git restore styles.css

# Or restore all changes at once:
# git restore .

# Check status - should be clean
git status
```

#### Step 8: Restore Files from Specific Commits

```bash
# Let's commit our current state first
git add .
git commit -m "Add feature file and update README"

# Now simulate accidentally deleting a file
rm styles.css

# Check status
git status

# Restore the file from the last commit
git restore styles.css

# Verify the file is back
ls -la styles.css

# You can also restore from a specific commit
# git restore --source=HEAD~2 filename.txt
```

**📝 Question 3:** What's the difference between `git restore --staged` and `git restore` without flags?

---

### Task 4: Branching and Merging

#### Step 9: Create and Work with Branches

```bash
# Check current branch
git branch

# Create a new branch for a feature
git checkout -b feature-contact-form

# Or use the newer syntax:
# git switch -c feature-contact-form

# Verify you're on the new branch
git branch

# Create a contact form
cat > contact.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Us</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Contact Us</h1>
    <form>
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
        
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        
        <label for="message">Message:</label>
        <textarea id="message" name="message" required></textarea>
        
        <button type="submit">Send Message</button>
    </form>
</body>
</html>
EOF

# Add form styling to CSS
cat >> styles.css << 'EOF'

/* Contact Form Styles */
form {
    max-width: 500px;
    margin: 20px auto;
}

label {
    display: block;
    margin-top: 10px;
    font-weight: bold;
}

input, textarea {
    width: 100%;
    padding: 8px;
    margin-top: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    background-color: #007acc;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    margin-top: 10px;
    cursor: pointer;
}

button:hover {
    background-color: #005999;
}
EOF

# Commit the changes on the feature branch
git add .
git commit -m "Add contact form with styling"

# View the log
git log --oneline --graph
```

#### Step 10: Merge the Feature Branch

```bash
# Switch back to main branch
git checkout main
# or: git switch main

# Notice the contact.html doesn't exist on main
ls -la

# Merge the feature branch
git merge feature-contact-form

# Check the log to see the merge
git log --oneline --graph

# Now the contact form is available on main
ls -la
```

#### Step 11: Practice Merge Conflicts

```bash
# Create a new branch
git checkout -b feature-navbar

# Modify the main HTML file
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav>
        <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="contact.html">Contact</a></li>
        </ul>
    </nav>
    
    <h1>Welcome to Git Practice</h1>
    <p>This is my first commit.</p>
    <p>Now I'm learning about multiple commits!</p>
    <p>Click the title for a surprise!</p>
    
    <script src="script.js"></script>
</body>
</html>
EOF

# Commit the navbar changes
git add .
git commit -m "Add navigation bar"

# Switch back to main and make conflicting changes
git checkout main

# Modify the same file differently
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice - Advanced</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Advanced Git Practice</h1>
    </header>
    
    <main>
        <p>This is my first commit.</p>
        <p>Now I'm learning about multiple commits!</p>
        <p>Click the title for a surprise!</p>
    </main>
    
    <script src="script.js"></script>
</body>
</html>
EOF

# Commit the conflicting changes
git add .
git commit -m "Add header and main sections with updated title"

# Now try to merge - this will create a conflict!
git merge feature-navbar
```

#### Step 12: Resolve Merge Conflicts

```bash
# Git will show a conflict message
# Check the status
git status

# Look at the conflicted file
cat index.html

# Edit the file to resolve conflicts (use VS Code for easier editing)
code index.html

# After resolving conflicts, the file should look like this:
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Git Practice - Advanced</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav>
        <ul>
            <li><a href="index.html">Home</a></li>
            <li><a href="contact.html">Contact</a></li>
        </ul>
    </nav>
    
    <header>
        <h1>Advanced Git Practice</h1>
    </header>
    
    <main>
        <p>This is my first commit.</p>
        <p>Now I'm learning about multiple commits!</p>
        <p>Click the title for a surprise!</p>
    </main>
    
    <script src="script.js"></script>
</body>
</html>
EOF

# Stage the resolved file
git add index.html

# Complete the merge
git commit -m "Resolve merge conflict between navbar and header features"

# View the final log
git log --oneline --graph
```

**📝 Question 4:** What are the steps to resolve a merge conflict? How do you know when a merge conflict has been resolved?

---

### Task 5: Advanced Git History and Inspection

#### Step 13: Explore Git History

```bash
# View detailed commit history
git log

# View one-line format
git log --oneline

# View graph format
git log --graph --oneline --all

# View commits with file changes
git log --stat

# View commits for a specific file
git log -- index.html

# View commits by author (use your name)
git log --author="Your Name"

# View commits in the last week
git log --since="1 week ago"

# Show the differences in a commit
git show HEAD

# Show differences for a specific commit (use actual commit hash)
git show [commit-hash]
```

#### Step 14: Compare Changes

```bash
# Compare working directory to last commit
git diff

# Compare staged changes to last commit
git diff --staged

# Compare two commits
git diff HEAD~2 HEAD

# Compare two branches
git diff main feature-navbar

# Show what files changed between commits
git diff --name-only HEAD~3 HEAD
```

#### Step 15: Find Changes with Git Blame and Git Grep

```bash
# See who changed what in a file
git blame index.html

# Search for content in files
git grep "contact"

# Search in specific commit
git grep "navbar" HEAD~1

# Search with line numbers
git grep -n "body"
```

**📝 Question 5:** How would you find out who last modified a specific line in a file?

---

## 🧪 Testing Your Knowledge

### Challenge 1: Undo Mistakes

1. Create a file called `mistake.txt` with some content
2. Commit it
3. Modify the file and commit again
4. Realize you want to completely remove both commits
5. Use the appropriate git command to remove both commits and the file

### Challenge 2: Cherry-pick a Commit

1. Create a branch called `experimental`
2. Make 3 commits on this branch
3. Switch back to main
4. Use `git cherry-pick` to bring only the middle commit to main

### Challenge 3: Interactive Rebase

1. Make 3 quick commits with typos in the commit messages
2. Use `git rebase -i HEAD~3` to fix the commit messages
3. Squash the last two commits into one

---

## 📝 Assignment Deliverables

### Submit the Following:

1. **Screenshot of your final git log:**
   ```bash
   git log --oneline --graph --all
   ```

2. **Answers to all questions (1-5) asked throughout the assignment**

3. **A brief summary (200-300 words) describing:**
   - The most challenging part of the assignment
   - Which Git command you found most useful
   - How you plan to use these Git skills in future projects

### Submission Format:

Create a file called `ASSIGNMENT_REPORT.md` in your repository with:

```markdown
# Git Assignment 1 Report

## Final Git Log
[Paste your git log --oneline --graph --all output here]

## Question Answers

### Question 1: Commit Count
[Your answer here]

### Question 2: Reset Differences
[Your answer here]

### Question 3: Restore Options
[Your answer here]

### Question 4: Merge Conflict Resolution
[Your answer here]

### Question 5: Finding File Changes
[Your answer here]

## Reflection

### Most Challenging Part
[Your reflection here]

### Most Useful Command
[Your thoughts here]

### Future Applications
[Your plans here]
```

---

## 🏆 Success Criteria

You have successfully completed this assignment when you can:

- [ ] Create and manage Git repositories
- [ ] Make meaningful commits with clear messages
- [ ] Use soft and hard reset appropriately
- [ ] Restore files from staging and working directory
- [ ] Create and merge branches
- [ ] Resolve merge conflicts
- [ ] Navigate Git history effectively
- [ ] Understand when and why to use each Git command

---

## 🆘 Getting Help

If you get stuck:

1. **Read the error messages carefully** - Git provides helpful information
2. **Use `git status`** - It often tells you what to do next
3. **Check the Git documentation:** `git help [command]`
4. **Ask for help** - Don't struggle alone!

---

## 🚀 Next Steps

After completing this assignment:

1. Practice these commands regularly in your daily development
2. Learn about Git hooks and advanced workflows
3. Explore Git GUI tools like GitKraken or Sourcetree
4. Study branching strategies like Git Flow

---

*🎉 **Congratulations!** You've mastered the fundamental Git commands that form the foundation of modern software development. These skills will serve you throughout your entire programming career.*

---

[← Back to Git Guide](git.md) | [← Back to Main Guide](readme.md)