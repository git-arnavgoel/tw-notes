# GitHub Notes

Git tracks versions locally on your computer, whereas GitHub is an online service that hosts Git repositories and provides Pull Requests, Issues, Projects and code review.

## Connecting and Pushing a Local Repo
Create an empty repository on GitHub (without README when pushing an existing local repo):
- git branch -M main
- git remote add origin https://github.com/USERNAME/repo.git
- git remote -v
- git push -u origin main

Push a tag:
- git push origin v1.0

## Cloning and Syncing
- git clone https://github.com/USERNAME/repo.git (downloads repository and history)
- git fetch origin (downloads remote commits without merging)
- git pull origin main (runs fetch and merges remote updates into current branch)

## Collaborative PR Workflow
1. Create and switch to a branch: git switch -c feature-branch
2. Make commits and push branch: git push -u origin feature-branch
3. Open a Pull Request (PR) on GitHub targeting main.
4. Review and merge the PR.
5. Update local main:
   - git switch main
   - git pull origin main

## Extra Concepts
- Fork vs Clone: Fork copies a repository to your GitHub account online so you can contribute back via PR. Clone downloads a repository to your local laptop.
- Issues: track bugs, tasks and feature requests.
- Projects: Kanban boards (Todo, In Progress, In Review, Done) connected to Issues and PRs.
- Auth and Security: HTTPS uses a Personal Access Token (PAT) or SSH keys. Use 2FA and never commit API keys or passwords.
