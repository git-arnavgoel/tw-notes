# Git Notes

Git is a Distributed Version Control System (DVCS) that tracks project files locally through commit snapshots instead of saving duplicate copies like final_v2_new.py.

## Three Main Areas
1. Working Directory - files you edit on disk
2. Staging Area (Index) - files queued via git add for the next commit
3. Local Repository (.git) - stored commit history

Each commit stores a hash ID, author name/email, timestamp, message and parent commit. Branches are pointers to commits so new features stay isolated from main.

## Commands from Class Slides

Setup:
- git --version
- git config --global user.name "Your Name"
- git config --global user.email "you@example.com"
- git config --global --list

Initialize and commit:
- mkdir lab-repo
- cd lab-repo
- git init
- git status
- git add prog.py (or git add *.py)
- git add .
- git commit -m "Add prog.py"

Logs, tracked files and diffs:
- git log
- git log --oneline
- git ls-files (lists tracked files in index)
- git diff (working directory vs staging)
- git diff --staged (staging vs last commit)
- git diff HEAD (all local changes vs last commit)

.gitignore, moving and removing:
Add patterns like __pycache__/, *.pyc, .env, *.log, data/ into .gitignore so Git skips temp files and secrets. Adding a pattern to .gitignore does not remove files that were already committed earlier.
- git mv old.py new.py (renames/moves file and stages it)
- git rm old.py (deletes tracked file and stages deletion)

Undoing changes:
- git restore --staged prog.py (unstages file without deleting edits)
- git restore prog.py (discards uncommitted edits permanently)
- git revert COMMIT_ID (undoes an older commit safely by recording a new reverse commit)

Branching, merging and rebasing:
- git branch
- git branch feature-ui
- git switch feature-ui
- git switch -c feature-ui
- git switch main
- git merge feature-ui

Merge conflicts occur when two branches modify the same lines. Git writes markers in the file:

```
<<<<<<< HEAD
...
=======
...
>>>>>>> feature-ui
```

Keep the lines you want, delete the marker lines, then run git add <file> and git commit.

git merge creates a merge commit and keeps true branching history. git rebase main (run inside the feature branch) replays commits linearly on top of main (avoid rebasing commits already pushed).

Tags:
- git tag
- git tag -a v1.0 -m "Release 1.0"
- git show v1.0
