# Git & GitHub Notes

## 1. Git vs GitHub

| Git                                        | GitHub                                                                                           |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| Git is a **version-control system (VCS)**. | GitHub is an **online platform for hosting Git repositories and collaborating**.                 |
| Runs on your computer.                     | Runs primarily online/cloud.                                                                     |
| Tracks project history.                    | Hosts repositories and provides collaboration features like Pull Requests, Issues, Reviews, etc. |

---

# 2. The 4 Important Places

The basic Git workflow can be understood through these four places:

```text
Your Files
    ↓
Working Directory
    ↓ git add
Staging Area
    ↓ git commit
Local Repository
    ↓ git push
GitHub Repository
```

### 1. Working Directory

The **actual project folder** where you work and modify files.

Example:

```text
my-project/
├── index.html
├── style.css
└── script.js
```

---

### 2. Staging Area

Git has an intermediate area called the **staging area**.

It allows us to choose **which changes should go into the next commit**.

```bash
git add .
```

or:

```bash
git add file1.js
```

---

### 3. Local Repository

After staging, `git commit` stores the changes as a **commit** in the local Git repository.

The local repository exists **on your computer**.

---

### 4. GitHub Repository

The GitHub repository is the **remote repository**.

```bash
git push
```

uploads commits from your local repository to the remote GitHub repository.

---

# 3. `git init`

Used to convert a normal folder into a **Git repository**.

```bash
git init
```

It creates a hidden `.git` directory.

```text
my-project/
├── index.html
├── style.css
└── .git/
```

The `.git` folder contains Git's repository information.

---

# 4. `git status`

Shows the current state of your Git repository.

```bash
git status
```

It can tell you about:

* Modified files
* Untracked files
* Staged files
* Current branch
* Commits ahead/behind the remote

Example:

```text
Changes not staged for commit:
    modified: app.js

Changes to be committed:
    modified: index.html
```

---

# 5. `git add`

After modifying files, use `git add` to put changes into the **staging area**.

### Stage one file

```bash
git add fileName
```

Example:

```bash
git add index.html
```

### Stage multiple files

```bash
git add file1.js file2.js
```

### Stage all changes

```bash
git add .
```

> **Important:** `git add` does **not** mean commit.

It only moves selected changes:

```text
Working Directory
       ↓
    git add
       ↓
Staging Area
```

---

# 6. `git commit`

After staging:

```bash
git add .
```

Create a commit:

```bash
git commit -m "initial commit"
```

A **commit is essentially a snapshot of the project at a particular point in time.**

Git stores the history of these snapshots, which makes it possible to move between different versions of the project.

Example:

```text
A ─── B ─── C
```

Each letter represents a commit/snapshot.

---

# 7. `git add` vs `git commit`

| `git add`                            | `git commit`                            |
| ------------------------------------ | --------------------------------------- |
| Selects changes for the next commit. | Saves staged changes as a Git snapshot. |
| Working Directory → Staging Area     | Staging Area → Local Repository         |
| Does not create a commit.            | Creates a commit.                       |

```text
Working Directory
       │
       │ git add
       ↓
Staging Area
       │
       │ git commit
       ↓
Local Repository
```

---

# 8. Why Not Directly Commit?

Suppose you modified 5 files:

```text
A.js
B.js
C.js
D.js
E.js
```

But you only want `A.js` and `B.js` in your next commit.

You can do:

```bash
git add A.js B.js
git commit -m "Update A and B"
```

The staging area gives you this control.

---

# 9. `git log`

Used to see previous commits.

```bash
git log
```

Shorter version:

```bash
git log --oneline
```

Example:

```text
a1b2c3d Add login page
e4f5g6h Fix navbar
i7j8k9l Initial commit
```

---

# 10. `.gitignore`

`.gitignore` tells Git **not to track specified files/folders**.

Example:

```text
node_modules/
.env
dist/
```

Typical `.gitignore`:

```gitignore
node_modules/
.env
dist/
```

This is especially useful for:

* Dependencies
* Environment variables
* Build files
* Temporary files
* IDE-generated files

---

# 11. Connecting Git to GitHub

After creating a GitHub repository, GitHub provides a repository URL.

Connect your local repository to it:

```bash
git remote add origin <github_repo_url>
```

Example:

```bash
git remote add origin https://github.com/username/my-project.git
```

---

# 12. Check Whether Git and GitHub Are Connected

Use:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/my-project.git (fetch)
origin  https://github.com/username/my-project.git (push)
```

This tells you that your local repository has a remote named `origin`.

---

# 13. What is `origin`?

`origin` is simply a **name/alias** referring to a remote repository.

Instead of repeatedly typing the complete URL:

```text
https://github.com/username/my-project.git
```

we can use:

```bash
origin
```

For example:

```bash
git push origin main
```

Think of it as:

```text
origin = "that remote GitHub repository"
```

> `origin` is only a conventional name. It is not a special keyword.

---

# 14. `git push`

Uploads commits from the **local repository → remote repository**.

```bash
git push origin main
```

Flow:

```text
Local Repository
       │
       │ git push
       ↓
GitHub Repository
```

---

# 15. `git pull`

Receives and integrates changes from the remote repository into your current local branch.

```bash
git pull
```

Conceptually:

```text
GitHub Repository
       │
       │ git pull
       ↓
Local Repository
```

---

# 16. `git fetch` vs `git pull`

### `git fetch`

Downloads information about changes from the remote repository.

```bash
git fetch
```

It does **not automatically integrate those changes into your current branch**.

### `git pull`

Conceptually:

```text
git pull
   =
git fetch
   +
integrate changes
```

So:

| Command     | Meaning                             |
| ----------- | ----------------------------------- |
| `git fetch` | Download remote changes/information |
| `git pull`  | Fetch + integrate changes           |

---

# 17. `git clone`

Used to get an existing Git repository onto your computer.

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/username/project.git
```

Flow:

```text
GitHub Repository
       ↓
   git clone
       ↓
Your Computer
```

---

# 18. `git clone` vs `git pull`

| `git clone`                                  | `git pull`                                      |
| -------------------------------------------- | ----------------------------------------------- |
| Used to get a repository for the first time. | Used to update an existing local repository.    |
| Creates a local copy of the repository.      | Brings new changes into an existing repository. |

Think:

```text
First time:
GitHub → clone → Computer

Later:
GitHub → pull → Existing Computer Repository
```

---

# 19. Branches

Branches allow you to work on different features independently.

Example:

```text
             feature-login
            /
main ──────●────────────
            \
             feature-cart
```

You can create a branch for a feature without directly modifying the `main` branch.

Common examples:

```text
main
feature-login
feature-payment
bugfix-navbar
```

---

# 20. `git branch`

### List branches

```bash
git branch
```

The current branch has a `*`:

```text
  feature-login
* main
```

### Create a branch

```bash
git branch branch_name
```

Example:

```bash
git branch feature-login
```

> `git branch` creates the branch but **does not switch to it**.

---

# 21. `git switch`

### Switch to another branch

```bash
git switch branch_name
```

Example:

```bash
git switch feature-login
```

### Create and switch to a branch

```bash
git switch -c feature-login
```

This performs both:

```text
Create branch
     +
Switch to branch
```

---

# 22. `git checkout`

Historically, `git checkout` was used for several purposes.

### Switch branches

```bash
git checkout branch_name
```

### Restore an older version of a file

```bash
git checkout <commit> -- fileName
```

Historically, `git checkout` was used for:

* Creating branches
* Switching branches
* Restoring files

Modern Git provides more focused commands:

```text
git switch  → branch operations
git restore → file restoration
```

---

# 23. `git switch -c` vs `git branch`

| `git branch`           | `git switch -c`                     |
| ---------------------- | ----------------------------------- |
| Creates a branch only. | Creates and switches to the branch. |

Example:

```bash
git branch feature-login
```

You remain on your current branch.

Whereas:

```bash
git switch -c feature-login
```

creates the branch **and immediately moves you to it**.

---

# 24. Merging

Suppose you have:

```text
main
  \
   feature
```

After completing the feature, switch to `main`:

```bash
git switch main
```

Then merge the feature:

```bash
git merge feature
```

Conceptually:

```text
       feature
      /
main ─────────●
               \
                merge
```

The feature's changes are integrated into `main`.

---

# 25. Merge Conflicts

A merge conflict can happen when Git cannot automatically determine which changes should be kept.

For example, two people modify the same part of a file differently.

Git may show:

```text
<<<<<<< HEAD
Your version
=======
Other version
>>>>>>> feature
```

You must manually decide what the final code should be.

Then:

```bash
git add .
git commit
```

---

# 26. `git rebase`

`git rebase` is another way of integrating changes.

Example:

```bash
git switch feature
git rebase main
```

It takes your feature commits and replays them on top of the latest `main`.

---

# 27. Merge vs Rebase

| Merge                                              | Rebase                                         |
| -------------------------------------------------- | ---------------------------------------------- |
| Preserves branching history.                       | Creates a more linear history.                 |
| Usually creates a merge commit when needed.        | Replays commits onto another base.             |
| Does not rewrite existing commits in the same way. | Rewrites commit history.                       |
| Generally safer for shared/public history.         | Be careful with already-pushed shared commits. |

Simplified:

### Merge

```text
A ─── B ─── C ───── M
      \           /
       D ─── E ───
```

### Rebase

```text
A ─── B ─── D' ─── E'
             \
              linear history
```

---

# 28. `git reset`

`git reset` moves the branch pointer backward.

It is mainly used to:

* Undo commits
* Unstage changes

The exact effect depends on the option used.

---

# 29. `git reset --soft HEAD~1`

Undo the last commit but **keep its changes staged**.

Before:

```text
A ─── B ─── C
            ↑
           HEAD
```

After:

```text
A ─── B
       ↑
      HEAD
```

But the changes introduced by `C` remain in the **staging area**.

```bash
git reset --soft HEAD~1
```

---

# 30. `git reset --mixed HEAD~1`

Undo the last commit.

The changes remain in your files, but they are **unstaged**.

```bash
git reset --mixed HEAD~1
```

Flow:

```text
Commit C
   ↓
removed from history

Changes
   ↓
Working Directory
```

`--mixed` is the default mode of `git reset`.

So:

```bash
git reset HEAD~1
```

is equivalent to:

```bash
git reset --mixed HEAD~1
```

---

# 31. `git reset --hard HEAD~1`

Undo the last commit and **discard the changes introduced by that commit from the working tree/index**.

```bash
git reset --hard HEAD~1
```

⚠️ **Be careful:** this can permanently discard work that is not otherwise saved.

---

# 32. `HEAD`

`HEAD` represents your **current position in the commit history**, normally the currently checked-out commit/branch tip.

Example:

```text
A ─── B ─── C
            ↑
           HEAD
```

### Previous commit

```bash
HEAD~1
```

### Two commits before

```bash
HEAD~2
```

So:

```text
HEAD      → current commit
HEAD~1    → one commit before
HEAD~2    → two commits before
```

---

# 33. `git revert`

`git revert` creates a **new commit that reverses the changes introduced by an earlier commit**.

Example:

Before:

```text
A ─── B ─── C
```

After reverting `C`:

```text
A ─── B ─── C ─── D
```

`D` is a new commit that reverses `C`.

Example:

```bash
git revert C
```

---

# 34. `reset` vs `revert`

| `git reset`                          | `git revert`                  |
| ------------------------------------ | ----------------------------- |
| Moves the branch/history pointer.    | Creates a new commit.         |
| Can rewrite history.                 | Preserves existing history.   |
| Can be dangerous on shared branches. | Safer for shared branches.    |
| Useful for local mistakes.           | Useful for published commits. |

Simple rule:

> **Private/local mistake → reset can be useful.**
> **Already-published/shared commit → revert is usually safer.**

---

# 35. `git restore`

`git restore` is primarily used for **restoring file contents or changing staging state**.

Example:

```bash
git restore file.js
```

This can restore the working-tree version of the file.

---

# 36. `git restore --staged`

Suppose:

```bash
git add file1.js
```

But you realize you don't want `file1.js` in the staging area.

Use:

```bash
git restore --staged file1.js
```

This **unstages** the file.

The changes are not deleted.

```text
Staging Area
     ↓
git restore --staged
     ↓
Working Directory
```

> Important: `git restore file1.js` and `git restore --staged file1.js` do different things.

---

# 37. `git restore` vs `git reset`

| `git restore`                                     | `git reset`                                                                         |
| ------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Primarily works with file contents/staging state. | Can move `HEAD`/branch history.                                                     |
| Useful for restoring files.                       | Useful for undoing commits.                                                         |
| `git restore --staged` unstages files.            | `git reset --soft/mixed/hard` has different effects on commits, staging, and files. |

---

# 38. `git stash`

Suppose you're working on `branch1`:

```text
branch1
```

You have unfinished changes.

Suddenly, you need to switch to another branch:

```bash
git switch main
```

But you don't want to commit the unfinished work.

You can temporarily save it using:

```bash
git stash
```

Git temporarily stores your uncommitted changes.

Later, bring them back:

```bash
git stash pop
```

Basic workflow:

```text
Uncommitted changes
        ↓
   git stash
        ↓
Working directory becomes clean
        ↓
Switch branch / do other work
        ↓
   git stash pop
        ↓
Changes restored
```

---

# 39. `git stash pop` vs `git stash apply`

| `git stash pop`                                  | `git stash apply`      |
| ------------------------------------------------ | ---------------------- |
| Restores the stash.                              | Restores the stash.    |
| Removes the stash entry if successfully applied. | Keeps the stash entry. |

Example:

```bash
git stash pop
```

versus:

```bash
git stash apply
```

---

# 40. Tags

Tags are used to identify important points/commits in history.

For example:

```bash
git tag v1.0.0
```

This can identify a release:

```text
A ─── B ─── C
          ↑
        v1.0.0
```

Push a tag to GitHub:

```bash
git push origin v1.0.0
```

---

# 41. GitHub Pull Request

A **Pull Request (PR)** is not a Git command.

It is a **GitHub collaboration feature**.

Typical workflow:

```text
main
 ↓
Create branch
 ↓
feature branch
 ↓
Make changes
 ↓
Commit
 ↓
Push branch to GitHub
 ↓
Create Pull Request
 ↓
Review
 ↓
Merge into main
```

---

# 42. Professional Git/GitHub Workflow

A common workflow:

### 1. Start from latest `main`

```bash
git switch main
git pull
```

### 2. Create a feature branch

```bash
git switch -c feature-name
```

### 3. Make changes

Work on your project.

### 4. Check changes

```bash
git status
```

### 5. Stage changes

```bash
git add .
```

### 6. Commit

```bash
git commit -m "Add feature"
```

### 7. Push the branch

```bash
git push -u origin feature-name
```

### 8. Create Pull Request

Go to GitHub and create a PR from:

```text
feature-name → main
```

### 9. Review and merge

After review, the PR can be merged into `main`.

---

# 43. What Does `-u` Mean?

In:

```bash
git push -u origin feature-name
```

`-u` means **set the upstream/tracking relationship**.

It tells Git:

```text
Local branch:
feature-name

tracks:

Remote branch:
origin/feature-name
```

After this, you can generally use:

```bash
git push
```

instead of:

```bash
git push origin feature-name
```

Similarly, you can use:

```bash
git pull
```

without specifying the remote and branch.

---

# 44. `git push` vs `git pull`

| `git push`       | `git pull`                      |
| ---------------- | ------------------------------- |
| Local → Remote   | Remote → Local                  |
| Uploads commits. | Fetches and integrates changes. |

```text
git push

Local Repository ─────────→ GitHub
```

```text
git pull

GitHub ──────────────────→ Local Repository
```

---

# 45. `git fetch` vs `git pull`

### Fetch

```bash
git fetch
```

Downloads remote information/commits but does not automatically merge them into your current branch.

### Pull

```bash
git pull
```

Conceptually:

```text
git pull
   =
git fetch
   +
integrate changes
```

---

# 46. `origin` vs `upstream`

This is especially important when working with **forks**.

Suppose:

```text
Original Project
      ↓
    Fork
      ↓
Your GitHub Repository
```

After cloning your fork:

```text
origin
   ↓
Your fork
```

And you can add the original repository as:

```text
upstream
   ↓
Original project
```

So commonly:

```text
origin   → your fork
upstream → original project
```

You can get updates from the original project using:

```bash
git fetch upstream
```

---

# 47. `fork` vs `clone`

| Fork                                                                          | Clone                                    |
| ----------------------------------------------------------------------------- | ---------------------------------------- |
| Creates a GitHub copy of someone else's repository under your GitHub account. | Downloads a repository to your computer. |
| Happens on GitHub.                                                            | Happens on your computer.                |
| Creates your own GitHub repository.                                           | Creates a local working copy.            |

Flow:

### Fork

```text
Original GitHub Repository
          ↓
        Fork
          ↓
Your GitHub Repository
```

### Clone

```text
GitHub Repository
       ↓
   git clone
       ↓
Your Computer
```

---

# 48. Fork + Clone + Pull Request

This is a common **open-source contribution workflow**.

```text
Original Project
       ↓
     Fork
       ↓
My GitHub Repository
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
My GitHub Repository
       ↓
Pull Request
       ↓
Original Project
```

---

# 49. `git diff`

Shows the **exact changes** that have not been staged.

```bash
git diff
```

For example, if you changed:

```javascript
let age = 20;
```

to:

```javascript
let age = 21;
```

`git diff` shows what changed.

---

# 50. `git diff` vs `git status`

| `git status`                           | `git diff`                       |
| -------------------------------------- | -------------------------------- |
| Gives an overview of what changed.     | Shows the exact content changes. |
| Shows modified/untracked/staged files. | Shows line-by-line differences.  |

### To see staged changes:

```bash
git diff --staged
```

Typical workflow:

```bash
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

# 51. `git show`

Used to inspect a particular commit.

```bash
git show <commit-id>
```

Example:

```bash
git show a1b2c3d
```

It shows information about the commit and what that commit changed.

---

# 52. `git remote`

A Git remote represents a **remote repository location** associated with your local Git repository.

### Show remote names

```bash
git remote
```

Example:

```text
origin
```

### Show remote URLs

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

### Add a remote

```bash
git remote add origin <repository-url>
```

### Change a remote URL

```bash
git remote set-url origin <new-repository-url>
```

### Remove a remote

```bash
git remote remove origin
```

Removing a remote only removes the **remote configuration from your local repository**. It does not delete the GitHub repository itself.

---

# 53. Working Directory vs Local Repository

| Working Directory                      | Local Repository                                     |
| -------------------------------------- | ---------------------------------------------------- |
| Actual project files.                  | Git's saved repository history/data.                 |
| Where you actively work, e.g. VS Code. | Stores commits, branches, objects, and Git metadata. |
| Changes happen here first.             | Contains Git's version history.                      |
| Example: `index.html`, `app.js`        | Example: `.git` directory                            |

Think:

```text
WORKING DIRECTORY
     ↓
Your actual files
     ↓
You edit them in VS Code


LOCAL REPOSITORY
     ↓
Git's version history
     ↓
Commits / branches / objects
```

---

# Quick Git Mental Model

The most important model to remember is:

```text
                 git add
Working ─────────────────→ Staging
  │                           │
  │                           │ git commit
  │                           ↓
  │                       Local Repo
  │                           │
  │                           │ git push
  │                           ↓
  │                       GitHub Repo
  │
  └──────── git restore
```

And to receive changes:

```text
GitHub
  │
  │ git fetch
  ↓
Remote-tracking information

GitHub
  │
  │ git pull
  ↓
Local Repository / Working Tree
```

---

# Most Important Commands

| Command             | Main Purpose                                 |
| ------------------- | -------------------------------------------- |
| `git init`          | Initialize Git repository                    |
| `git status`        | Check repository status                      |
| `git add`           | Stage changes                                |
| `git commit`        | Create a commit                              |
| `git log`           | View commit history                          |
| `git diff`          | View unstaged changes                        |
| `git diff --staged` | View staged changes                          |
| `git show`          | Inspect a commit                             |
| `git branch`        | View/create branches                         |
| `git switch`        | Switch branches                              |
| `git switch -c`     | Create + switch branch                       |
| `git merge`         | Merge branches                               |
| `git rebase`        | Rebase commits                               |
| `git reset`         | Move HEAD/history and/or unstage             |
| `git revert`        | Create a commit that reverses another commit |
| `git restore`       | Restore file contents/staging state          |
| `git stash`         | Temporarily store uncommitted changes        |
| `git tag`           | Mark important commits                       |
| `git remote`        | Manage remote repositories                   |
| `git fetch`         | Download remote changes/information          |
| `git pull`          | Fetch + integrate                            |
| `git push`          | Upload commits                               |
| `git clone`         | Copy a repository to your computer           |

---

# Open-Source Mental Model

For your own repository:

```text
Local Repository
      ↕
   origin
      ↕
GitHub Repository
```

For contributing to someone else's project:

```text
Original Repository
       ↑
   Pull Request
       ↑
Your GitHub Fork
       ↑
     origin
       ↑
Your Computer

Your Computer
       ↑
    upstream
       ↑
Original Repository
```

The key distinction is:

```text
Git       → version control
GitHub    → hosting + collaboration

Working Directory → actual files
Staging Area      → selected changes
Local Repository  → committed history
Remote Repository → GitHub copy
```
