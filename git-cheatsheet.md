# Git & GitHub cheatsheet

## Setup

```
git init                              # Initialize a new repo
git clone <url>                       # Download an existing repo
git remote add origin <url>           # Link local repo to GitHub
git remote set-url origin <url>       # Change remote URL
```

## SSH keys

```
ssh-keygen -t ed25519 -C "email"      # Generate SSH key pair
eval "$(ssh-agent -s)"                # Start SSH agent
ssh-add ~/.ssh/id_ed25519             # Add private key to agent
pbcopy < ~/.ssh/id_ed25519.pub        # Copy public key to clipboard
ssh -T git@github.com                 # Test SSH connection
```

## Daily workflow

```
git status                            # See what changed
git add .                             # Stage all changes
git add <file>                        # Stage specific file
git commit -m "message"               # Save snapshot with description
git push                              # Upload to GitHub
git pull                              # Download latest from GitHub
```

## Branching

```
git checkout -b <branch-name>         # Create and switch to new branch
git checkout <branch-name>            # Switch to existing branch
git branch                            # List all branches
git merge <branch-name>               # Merge branch into current branch
git push -u origin <branch-name>      # Push new branch to GitHub
```

## History

```
git log                               # Full commit history
git log --oneline                     # Compact commit history
git diff                              # See unstaged changes
```

## Useful extras

```
git stash                             # Temporarily shelve changes
git reset <file>                      # Unstage a file
```

## .gitignore

Create a `.gitignore` file in your repo root to exclude files from tracking:

```
.env                                  # Secret keys and tokens
node_modules/                         # npm packages
*.log                                 # Log files
.DS_Store                             # macOS junk
```

## Merge conflicts

When Git shows conflict markers in a file:

```
<<<<<<< HEAD
your current branch version
=======
incoming branch version
>>>>>>> branch-name
```

Fix: delete the markers, keep the code you want, then:

```
git add .
git commit -m "resolve merge conflict"
git push
```

## Pull requests (on GitHub)

1. Push your branch: `git push -u origin <branch-name>`
2. Go to your repo on GitHub
3. Click "Compare & pull request"
4. Add title and description
5. Click "Create pull request"
6. Click "Merge pull request" after review

## Auto-close issues from commits

```
git commit -m "fix bug, closes #1"    # Closes issue #1 on merge
```
