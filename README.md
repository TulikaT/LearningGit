# Git & GitHub Notes

## 1. Git vs GitHub

* **Git** → Version-control system.
* **GitHub** → Online platform for hosting Git repositories and collaborating.

---

## 2. The 4 Important Places

```text
Your Files
    ↓
Working Directory        → actual project folder
    ↓ git add
Staging Area             → Git has an intermediate area called the staging area.
                            We choose which changes should go into next commit.
    ↓ git commit
Local Repository         → staged changes are stored in local Git repository.
                            This repository exists on our computer.
    ↓ git push
GitHub Repository        → Remote Repository / GitHub
```

---

## 3. `git init`

Used to convert a normal folder into a Git repository.

```bash
git init
```

---

## 4. `git status`

Tells about:

* Modified files
* Untracked files
* Staged files
* Current branch
* Commits ahead/behind remote

```bash
git status
```

---

## 5. `git add`

After modification, stage files:

```bash
git add fileName
```

Stage multiple files:

```bash
git add file1 file2
```

Stage all files at once:

```bash
git add .
```

> `git add` **does not mean commit**. It puts changes into the **staging area**.

---

## 6. `git commit`

After staging:

```bash
git add .
```

Create a commit:

```bash
git commit -m "initial commit"
```

* Git stores the snapshot of different commits.
* Hence, switching between different commits is possible.
* A **commit is essentially a snapshot of the project at a particular time**.

---

## 7. `git add` vs `git commit`

| `git add`                      | `git commit`                          |
| ------------------------------ | ------------------------------------- |
| Select changes for next commit | Save staged changes as a Git snapshot |

---

## 8. Why Not Directly Commit?

Might modify **5 files** but only want **2 files** for the next commit.

The staging area allows us to select only those 2 files.

---

## 9. `git log`

To see previous commits:

```bash
git log
```

Shorter version:

```bash
git log --oneline
```

---

## 10. `.gitignore`

Tells Git **not to track these files**.

```text
.gitignore
```

---

## 11. Connecting Git to GitHub

GitHub provides a repository URL when creating a repo.

Connect it to the local repo:

```bash
git remote add origin <github_repo_link>
```

---

## 12. Check if Both Are Connected

```bash
git remote -v
```

Output:

```text
origin  repo_link (fetch)
origin  repo_link (push)
```

---

## 13. What is `origin`?

Simply a **name/alias** referring to the main GitHub repo.

Instead of typing the complete repo URL, we use:

```bash
git push origin main
```

> `origin` = name referring to the remote repository.

---

## 14. `git push`

Upload commits from local repository to GitHub repository:

```bash
git push origin main
```

```text
Local Repository → GitHub Repository
```

---

## 15. `git pull`

Receive/integrate changes from GitHub into the local repository's current branch.

```bash
git pull
```

```text
GitHub Repository → Local Repository
```

---

## 16. `git fetch` vs `git pull`

| `git fetch`                    | `git pull`                           |
| ------------------------------ | ------------------------------------ |
| Tells/downloads remote changes | Fetch + integrate changes into local |

---

## 17. `git clone`

Used to get a GitHub repository into the local computer.

```bash
git clone <repo_url>
```

---

## 18. `git clone` vs `git pull`

| `git clone`                         | `git pull`                          |
| ----------------------------------- | ----------------------------------- |
| Get a repository for the first time | Update an existing local repository |

---

## 19. Branches

Branches allow you to work on different features independently.

```text
main
 ├── feature-1
 ├── feature-2
 └── feature-3
```

---

## 20. `git branch`

List all branches:

```bash
git branch
```

Current branch has `*` sign.

Create a branch:

```bash
git branch branch_name
```

---

## 21. `git switch`

Switch to another branch:

```bash
git switch branch_name
```

Create and switch:

```bash
git switch -c branch_name
```

---

## 22. `git checkout`

Switch to another branch:

```bash
git checkout branch_name
```

Restore an old version of files:

```bash
git checkout <commit> -- <file>
```

Historically, `git checkout` was used for **creating, switching and restoring**.

Now different commands are preferred:

* `git switch` → branch switching
* `git restore` → restoring files

---

## 23. `git switch -c` vs `git branch`

| `git branch`        | `git switch -c`                |
| ------------------- | ------------------------------ |
| Creates branch only | Creates and switches to branch |

---

## 24. Merging

First switch to main:

```bash
git switch main
```

Then merge the branch:

```bash
git merge branch_name
```

---

## 25. Merge Conflicts

If 2 people modify the **same part of a file**, Git doesn't know which version to keep.

This has to be resolved manually.

---

## 26. `git rebase`

Like merge, rebase integrates changes:

```bash
git rebase main
```

---

## 27. Merge vs Rebase

| Merge                       | Rebase                        |
| --------------------------- | ----------------------------- |
| Preserves branching history | Creates a more linear history |

---

## 28. `git reset`

Moves branch pointer backward.

Mainly used to:

* Undo commits
* Unstage changes

Depending on the option used.

---

## 29. `git reset --soft HEAD~1`

Undo the last commit, but **keep its changes staged**.

```text
A---B---C
     ↓
A---B

C changes remain staged
```

```bash
git reset --soft HEAD~1
```

---

## 30. `git reset --mixed HEAD~1`

Undo the last commit, keep the changes in files, but **unstage them**.

```text
C changes remain in Working Directory
```

```bash
git reset --mixed HEAD~1
```

---

## 31. `git reset --hard HEAD~1`

Undo the last commit and **discard changes**.

```bash
git reset --hard HEAD~1
```

> ⚠️ Be careful: changes can be lost.

---

## 32. `HEAD`

* `HEAD` → current commit
* `HEAD~1` → 1 commit before HEAD
* `HEAD~2` → 2 commits before HEAD

```text
A---B---C
        ↑
       HEAD

HEAD~1 → B
HEAD~2 → A
```

---

## 33. `git revert`

Creates a **new commit** that reverses the old commit.

```text
A---B---C  →  A---B---C---D
```

`D` reverses the changes made by `C`.

---

## 34. `reset` vs `revert`

| `reset`                      | `revert`                     |
| ---------------------------- | ---------------------------- |
| Moves history pointer        | Creates a new commit         |
| Can rewrite history          | Preserves history            |
| Dangerous on shared branches | Safer for shared branches    |
| Useful for local mistakes    | Useful for published commits |

---

## 35. `git restore`

Primarily used for **restoring files**.

```bash
git restore fileName
```

---

## 36. `git restore --staged`

Suppose:

```bash
git add file1
```

But you don't want to stage it.

Use:

```bash
git restore --staged file1
```

This **unstages** it.

---

## 37. `restore` vs `reset`

| `git restore`                         | `git reset`                                                     |
| ------------------------------------- | --------------------------------------------------------------- |
| Restore file contents / staging state | Move HEAD / branch history and possibly affect staging/worktree |

---

## 38. `git stash`

Working on `branch1` with unfinished changes, and suddenly you need to switch to another branch.

If changes aren't ready to commit:

```bash
git stash
```

Git temporarily stores uncommitted changes.

Bring changes back:

```bash
git stash pop
```

---

## 39. `git stash pop` vs `git stash apply`

| `git stash pop`                                                       | `git stash apply`                        |
| --------------------------------------------------------------------- | ---------------------------------------- |
| Restores stash and removes it from stash list if successfully applied | Restores stash but keeps the stash entry |

---

## 40. Tags

Used to identify important commits.

```bash
git tag v1.0.0
```

Push tag:

```bash
git push origin v1.0.0
```

---

## 41. GitHub Pull Request

Pull Request is **not a Git command**.

It is a **GitHub collaboration feature**.

Typical workflow:

```text
main
 ↓
create branch
 ↓
branch1
 ↓
make commits
 ↓
push branch
 ↓
GitHub
 ↓
Pull Request
 ↓
Review
 ↓
Merge
```

---

## 42. Professional Workflow

```bash
git switch main
git pull
git switch -c branch_name

# make changes

git status
git add .
git commit -m "commit1"
git push -u origin branch_name
```

Then:

```text
Create PR on GitHub
        ↓
      main
```

---

## 43. What does `-u` mean?

```bash
git push -u origin branch_name
```

`-u` establishes an **upstream tracking relationship**.

After this, simply use:

```bash
git push
```

instead of:

```bash
git push origin branch_name
```

---

## 44. `git push` vs `git pull`

| `git push`     | `git pull`     |
| -------------- | -------------- |
| Local → Remote | Remote → Local |

---

## 45. `fetch` vs `pull`

| `git fetch`                 | `git pull`                |
| --------------------------- | ------------------------- |
| Download remote information | Fetch + integrate changes |

---

## 46. `origin` vs `upstream`

With a fork:

```text
Original Project
      ↓ fork
My GitHub Repo
```

* **origin** → your fork
* **upstream** → original project

```bash
git fetch upstream
```

Gets updates from the original project.

---

## 47. `fork` vs `clone`

| Fork                                            | Clone                                  |
| ----------------------------------------------- | -------------------------------------- |
| Create GitHub copy of someone else's repository | Download a repository to your computer |
| GitHub → GitHub                                 | GitHub → Computer                      |

```text
Fork:
Original GitHub Repo → Fork → My GitHub Repo

Clone:
GitHub Repo → git clone → My Computer
```

---

## 48. Fork + Clone + PR

Standard open-source flow:

```text
Original Project
      ↓
     Fork
      ↓
My GitHub Repo
      ↓
    Clone
      ↓
My Computer
      ↓
Create Branch
      ↓
Make Changes
      ↓
Commit
      ↓
Push
      ↓
Pull Request
      ↓
Original Project
```

---

## 49. `git diff`

Shows changes that **haven't been staged**.

```bash
git diff
```

---

## 50. `git diff` vs `git status`

| `git status`                 | `git diff`           |
| ---------------------------- | -------------------- |
| What changed / what's staged | Exactly what changed |

For staged changes:

```bash
git diff --staged
```

Typical workflow:

```text
git status
    ↓
git diff
    ↓
git add .
    ↓
git diff --staged
    ↓
git commit
```

---

## 51. `git show`

Inspect a particular commit:

```bash
git show <commit-id>
```

Shows what that commit changed.

---

## 52. `git remote`

GitHub repositories are called **remote repositories**.

```bash
git remote
```

Shows names/aliases of remote repositories.

### View remote repositories

```bash
git remote -v
```

### Connect local repo with GitHub repo

```bash
git remote add origin <github_repo>
```

### Change URL

```bash
git remote set-url origin <new_repo_url>
```

### Remove remote

```bash
git remote remove origin
```

This removes the remote configuration from the **local repository**.

---

## 53. Working Directory vs Local Repository

| Working Directory                        | Local Repository                                          |
| ---------------------------------------- | --------------------------------------------------------- |
| Actual project files                     | Git's saved history                                       |
| Folder where we actively work in VS Code | Contains Git information about commits, branches, objects |
| Files we modify directly                 | `.git` directory                                          |

```text
Working Directory
      ↓
Actual project files
      ↓
Where we work in VS Code


Local Repository
      ↓
Git's saved history
      ↓
Commits + branches + objects
```
