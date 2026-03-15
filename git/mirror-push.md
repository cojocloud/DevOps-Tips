# The DevOps Mirror Push Trick

## You configure one remote with multiple push URLs.

Your repo will:

Fetch from GitHub

Push to GitHub

Push to GitLab

All with one command.
---
## Step 1 — Check Current Remote

Inside your repo:
```
git remote -v
```
Example output:
```
origin  git@github.com:cojocloud/bankapp.git (fetch)
origin  git@github.com:cojocloud/bankapp.git (push)
```
---
## Step 2 — Add GitLab as a Second Push Destination
```
git remote set-url --add --push origin git@github.com:cojocloud/bankapp.git
git remote set-url --add --push origin git@gitlab.com:cojocloud/bankapp.git
```
Now your repo has two push targets.

---
## Step 3 — Verify the Configuration
```
git remote -v
```
Expected output:
```
origin  git@github.com:cojocloud/bankapp.git (fetch)
origin  git@github.com:cojocloud/bankapp.git (push)
origin  git@gitlab.com:cojocloud/bankapp.git (push)
```
Notice:

fetch → GitHub

push → GitHub + GitLab

---
## Step 4 — Push once to Both Remotes Simultaneously
```
git push
```
This command will push your commits to both GitHub and GitLab at the same time. Both repos update simultaneously. 🔥
Example DevOps Workflow

Everyday development becomes:
```
git add .
git commit -m "new feature"
git push
```
Your code automatically updates:

- GitHub repo

- GitLab repo

---
## Real DevOps Use Case

Engineers often use this architecture:
```
Developer Laptop
       │
       ▼
GitHub (source control)
       │
       ▼
GitLab (CI/CD pipelines)
       │
       ▼
Kubernetes / EKS deployment
```
## This allows you to:

- keep GitHub public repo

- run GitLab CI/CD

- maintain redundant backup

## Optional: Confirm Push URLs

You can inspect them directly:
```git remote get-url --all origin
   git remote get-url --push origin
```
---
## Example:
```
git@github.com:cojocloud/bankapp.git
git@gitlab.com:cojocloud/bankapp.git
```
---

## Conclusion
The mirror push trick is a simple yet powerful way to maintain multiple remotes with a single push command. It’s ideal for:
- Redundant backups
- Multi-platform CI/CD
- Collaborative projects across different hosting services
By configuring your Git remotes this way, you can streamline your workflow and ensure your code is always up-to-date across all platforms. Happy coding! 🚀