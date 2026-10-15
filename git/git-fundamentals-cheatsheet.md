# Git & GitHub Fundamentals — Complete Beginner Cheatsheet

> Reference summary based on Coder Coder's [Learn Git & GitHub for Beginners Tutorial](https://www.youtube.com/watch?v=h2a3Kw-I_Ec).

---

## 1. Core Architecture & Mental Model
* **Working Directory:** The folder on your computer where you write and edit code [00:10:29].
* **Staging Area:** The preparation area where Git holds file snapshots before saving [00:15:07].
* **Local Repository (`.git` folder):** The hidden database storing your commits and project history locally [00:10:15].
* **Remote Repository (GitHub):** The online backup used to share code and collaborate across machines [00:01:05].

---

## 2. One-Time Setup & Privacy Configuration
Run these once when configuring Git on a new computer [00:04:08]:


## 3. Initializing a Repository
```bash

# Set your public Git author name
git config --global user.name "YourUsername"

# Use your GitHub private no-reply email to keep your personal email private
git config --global user.email "ID+username@users.noreply.github.com"

# Verify configured global settings (press 'q' to exit the list)
git config --list


Bash
# Navigate to your project folder
cd path/to/project

# Turn folder into a tracked Git repository (creates .git)
git init

# View directory contents including hidden files (.git)
ls -a
```

## 4. The Daily Development Workflow
Step A: Check Status & Inspect Changes
```Bash
# Check the status of modified, staged, or untracked files
git status

# Inspect unstaged line-by-line differences in your working directory
git diff

# Inspect changes already in the staging area vs last commit
git diff --staged
```
Step B: Stage & Snapshot
```bash
# Stage specific files
git add file1.py file2.md

# Stage all modified and new files in the current folder
git add .

# Create a snapshot with a descriptive message
git commit -m "feat(python): add pandas data cleaning script"

# Shortcut: Stage tracked modified files and commit in one step
git commit -am "fix: update database connection timeout"
```

## 5. Ignoring Files (.gitignore)
````bash
Code snippet
# Ignore sensitive credential and environment files
.env
*.local

# Ignore build output folders (trailing slash specifies folder)
build/
dist/

# Ignore virtual environments & python caches
__pycache__/
.venv/
````

## 6. Undoing Mistakes Safely

Discard unstaged changes: Restore a file back to the last commit [00:32:39]:

````Bash
git restore filename.py
````
**View History:**
````Bash
# Standard commit log (press 'q' to exit)
git log
# Compact, one-line log showing commit hashes and messages
git log --oneline
````
Revert a commit cleanly: Creates a new commit that inverts previous changes without rewriting Git history [00:38:17]:
````Bash
git revert <commit-hash>
````
## 7. Branching & Merging (Feature Branches)
Never work directly on main when testing new experiments [00:40:09]:
````Bash
# List all local branches (active branch marked with *)
git branch

# Create and switch to a new branch in one command
git switch -c feature-agent-rag

# Switch between existing branches
git switch main
git switch feature-agent-rag

# Merge changes into target branch (must be on main first)
git switch main
git merge feature-agent-rag

# Delete the feature branch once merged
git branch -d feature-agent-rag
````
## 8. Connecting Local Repositories to GitHub
When linking a pre-existing local repository to a fresh, empty GitHub repository (created with no README, license, or .gitignore on GitHub) [00:48:18]:
````Bash
# 1. Link your local project to the remote GitHub URL
git remote add origin [https://github.com/](https://github.com/)<username>/<repo-name>.git

# 2. Push local commits and set origin/main as default upstream
git push -u origin main

# 3. Future pushes from this branch only require:
git push
````