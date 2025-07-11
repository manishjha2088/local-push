This is my first commit
I am taching git and learning merge and rebasing


# Git Command History with Comments

Each command is explained for better understanding:

```powershell
git log --patch                       # Show detailed commit history with code changes (patches)
cls                                   # Clear the PowerShell screen
cd "C:\Users\Manish.Jha\OneDrive\Desktop\git-website"  # Navigate to project directory
git init                              # Initialize a new Git repository in the current directory
git add .                             # Stage all changes for the next commit
git commit -m "Initial commit"        # Commit staged changes with a message
git remote add origin https://github.com/yourusername/git-website.git  # Add remote GitHub repository (first attempt)
git push -u origin main               # Push the main branch to GitHub and set upstream (fails if 'main' doesn't exist)

git remote set-url origin https://github.com/manishjha2088/local-push.git  # Update the remote URL
git push -u origin main               # Push to remote 'main' branch (again fails if branch is named 'master')
git branch                            # List local branches and show current branch with '*'
git push -u origin master             # Correct push to GitHub using 'master' branch
git config --global user.email "uername@email.com"   # Set global email for git commits
git config --global user.name "Manish Jha"            # Set global username for git commits
git checkout -b feature/new-release   # Create and switch to a new branch called 'feature/new-release'
git merge feature/new-release         # Merge changes from 'feature/new-release' into current branch 
git branch -d feature/new-release     # Delete the 'feature/new-release' branch
git checkout -b bugfix/hotfix         # Create and switch to a new bugfix branch
git commit -m "added table cell"      # Commit changes made in this branch
git checkout -b bugfix/table-2        # Create another bugfix branch
git commit -m "added a table-2"       # Commit changes
git rebase master                     # Rebase current branch changes onto master for cleaner history
git merge bugfix/table-2              # Merge the 'bugfix/table-2' branch into the current branch 
```
