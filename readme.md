This is my first commit
I am teaching git and learning merge and rebasing


# Git Command History with Comments

# --- Session Setup & Initialization ---

# Clear your terminal screen for a fresh start.
cls

# Navigate to your project directory. Replace with your actual path.
cd "C:\Users\abc\Desktop\git-website"

# Initialize a brand new Git repository in the current directory.
# This creates a hidden .git folder to track all your project's changes.
git init

# --- Configuring Git (Important for your commits!) ---

# Set your global email address for Git commits. This identifies you in the commit history.
git config --global user.email "yourusername@email.com"

# Set your global username for Git commits. This is displayed alongside your email.
git config --global user.name "Your Name"

# --- Staging & Committing Your First Changes ---

# Add all current changes in your working directory to the staging area.
# The staging area is where you prepare changes for your next commit.
git add .

# Commit your staged changes with a descriptive message.
# This creates a snapshot of your project at this point in time.
git commit -m "Initial project setup and files"

# --- Connecting to a Remote Repository (GitHub/GitLab/Bitbucket) ---

# Link your local repository to a remote repository on GitHub (or similar).
# 'origin' is a conventional alias for your primary remote.
# Replace the URL with your actual GitHub repository URL.
git remote add origin https://github.com/yourusername/your-repo-name.git

# Verify that your remote repository has been added correctly.
git remote -v

# Push your 'main' (or 'master') branch from your local repository to the 'origin' remote.
# The '-u' flag sets 'origin main' as the upstream, so future 'git push' commands are simpler.
# Note: GitHub typically uses 'main' as the default branch name for new repos.
git push -u origin main

# If your remote branch is named 'master' (common in older repos), you'd use:
# git push -u origin master

# --- Viewing Your History ---

# Show a concise log of commits.
git log

# Show a detailed commit history, including the actual code changes (patches) for each commit.
# This is great for understanding what changed in each commit.
git log --patch

# Show a graphical representation of your commit history, very useful for seeing branches and merges.
git log --all --decorate --oneline --graph

# --- Branching: Isolating Development Efforts ---

# List all local branches and indicate which branch you are currently on with an asterisk (*).
git branch

# Create a new branch called 'feature/new-homepage' and immediately switch to it.
# This is where you'd develop a new feature without affecting the main codebase.
git checkout -b feature/new-homepage

# (Simulate making changes, e.g., adding a new file or modifying existing ones)
# New change 1...
# New change 2...

# Stage all changes within the 'feature/new-homepage' branch.
git add .

# Commit the changes made on this feature branch.
git commit -m "Implement basic homepage layout"

# Switch back to the 'main' branch to prepare for merging.
git checkout main

# --- Merging: Integrating Changes ---

# Merge changes from 'feature/new-homepage' into your current branch ('main').
# This creates a new merge commit, preserving the history of both branches.
git merge feature/new-homepage

# (After merging, you might want to clean up your local branches)

# Delete the 'feature/new-homepage' branch. You can only delete a branch
# if you are not currently on it and its changes have been merged.
git branch -d feature/new-homepage

# --- Hotfixes & More Branching ---

# Create and switch to a new branch specifically for a bugfix.
git checkout -b bugfix/login-issue

# (Simulate making a quick fix, e.g., correcting a typo in a login form)
# Fix the login bug...

# Commit the bugfix changes.
git commit -m "Fix: Resolved login form submission error"

# Push your bugfix branch to the remote if you're working with others.
# git push origin bugfix/login-issue

# Switch back to main to integrate the hotfix.
git checkout main

# Merge the bugfix directly into main.
git merge bugfix/login-issue

# Delete the bugfix branch after it's merged.
git branch -d bugfix/login-issue

# --- Rebasing: Rewriting History for a Cleaner Log ---

# IMPORTANT: Only rebase on branches you haven't pushed to a shared remote!
# Rebasing rewrites commit history, which can cause problems for collaborators.

# Let's create a new feature branch to demonstrate rebase.
git checkout -b feature/refactor-css

# (Make some initial changes on feature/refactor-css)
# git add .
# git commit -m "Refactor initial CSS for consistency"

# Now, imagine someone else pushed changes to 'main' while you were working.
# Let's simulate a commit on 'main' for demonstration purposes.
# git checkout main
# (Make a dummy commit on main, e.g., touch dummy.txt; git add .; git commit -m "Another change on main")
# git checkout feature/refactor-css

# Rebase the current branch ('feature/refactor-css') onto 'main'.
# This effectively moves your branch's base to the tip of 'main', making it appear
# as if you started your work after the latest 'main' changes.
# It results in a linear history, avoiding a merge commit.
git rebase main

# If there are conflicts during rebase, Git will pause and tell you to resolve them.
# After resolving:
# git add .             # Stage the resolved files
# git rebase --continue # Continue the rebase process

# Once rebase is complete and conflicts are resolved, you can merge into main.
git checkout main
git merge feature/refactor-css # This will be a fast-forward merge if no new commits were made on 'main' since the rebase.

# Clean up the feature branch.
git branch -d feature/refactor-css

# --- Undoing Changes (Crucial for learning!) ---

# View the status of your working directory (untracked, modified, staged files).
git status

# Unstage a file that was added to the staging area.
git reset HEAD <file-name>

# Discard changes in your working directory for a specific file.
# USE WITH CAUTION: This permanently removes local, uncommitted changes.
git checkout -- <file-name>

# Undo the last commit (keeps changes in working directory).
git reset HEAD~1

# Undo the last commit (discards changes, makes working directory match previous commit).
# USE WITH EXTREME CAUTION! This can lead to data loss if not understood.
git reset --hard HEAD~1

# Create a new commit that undoes the changes of a previous commit.
# This is safer for shared branches as it doesn't rewrite history.
# First, find the commit hash you want to revert: git log --oneline
# Then:
# git revert <commit-hash>
