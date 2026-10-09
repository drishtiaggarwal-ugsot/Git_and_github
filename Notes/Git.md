# 🔧 Git — Complete Beginner's Notes

> **Git is a Distributed Version Control System.** It tracks changes to files over time so you can see history, undo mistakes, work on multiple versions at once, and collaborate without overwriting each other's work.

---

## 📑 Table of Contents

1. [What Is Git?](#1-what-is-git)
2. [Why Use Git?](#2-why-use-git)
3. [A Tiny Bit of History](#3-a-tiny-bit-of-history)
4. [Key Vocabulary](#4-key-vocabulary)
5. [How Git Works — The 3 Areas](#5-how-git-works--the-3-areas)
6. [The Basic Workflow](#6-the-basic-workflow)
7. [Essential Commands](#7-essential-commands)
8. [Branching & Merging](#8-branching--merging)
9. [Merge Conflicts](#9-merge-conflicts)
10. [Undoing Things](#10-undoing-things)
11. [.gitignore](#11-gitignore)
12. [Common Misconceptions](#12-common-misconceptions)
13. [Common Mistakes & Fixes](#13-common-mistakes--fixes)
14. [Best Practices](#14-best-practices)
15. [Student Contributions](#15-student-contributions)

---

## 1. What Is Git?

Git is a tool that runs **on your own computer**. It watches a folder (called a **repository**) and lets you save "snapshots" of every file in it at any point in time. Each snapshot is called a **commit**.

Think of it like a video game save system: you can save your progress, keep playing, and if something goes wrong, load an earlier save.

**"Distributed"** means every person who has a copy of the repo has the **full history**, not just the latest files. There's no single central server that Git depends on.

### Key Features

- ✅ Tracks every change: who changed what, when, and why
- ✅ Branching & merging: work on features in isolation, then combine them
- ✅ Works offline: commit, branch, view history with no internet
- ✅ Fast and lightweight: most operations are local and instant
- ✅ Data integrity: every commit is identified by a cryptographic hash, so history can't silently get corrupted

---

## 2. Why Use Git?

| Without Git | With Git |
|-------------|----------|
| `project_final.zip`, `project_final_v2.zip`, `project_REALLY_final.zip` | One folder, full history inside |
| "Who broke this?" — no idea | `git log` and `git blame` tell you exactly |
| Emailing files back and forth | Everyone works on their own copy and merges |
| Afraid to try new ideas in case you break things | Make a branch, experiment freely, delete it if it fails |
| Lost work after a mistake | Go back to any previous commit |

---

## 3. A Tiny Bit of History

- Created by **Linus Torvalds** in **2005**, the same person who created Linux.
- Built because the Linux kernel team lost access to their previous version-control tool (BitKeeper).
- Designed to be fast, distributed, and able to handle huge projects with thousands of contributors.
- Today it's the most widely used version-control system in the world.

---

## 4. Key Vocabulary

| Term | Meaning |
|------|---------|
| **Repository (repo)** | A folder tracked by Git. The history lives in a hidden `.git` folder inside it. |
| **Commit** | A saved snapshot of your project at a moment in time, with a message describing it. |
| **Hash / SHA** | A unique ID for each commit, like `a1b2c3d`. |
| **Branch** | An independent line of work. Technically, just a movable pointer to a commit. |
| **main / master** | The default branch name. Newer repos use `main`. |
| **HEAD** | A pointer to "where you are right now", usually the latest commit of your current branch. |
| **Staging area (index)** | A waiting room where you choose which changes go into the next commit. |
| **Working directory** | The actual files you see and edit. |
| **Remote** | A copy of the repo somewhere else (e.g., on GitHub). Default name: `origin`. |
| **Clone** | Download a full copy of a remote repo, including history. |
| **Merge** | Combine changes from one branch into another. |
| **Conflict** | When Git can't automatically merge because two changes touch the same lines. |
| **Push / Pull** | Send commits to / get commits from a remote. |

---

## 5. How Git Works — The 3 Areas

```
 ┌────────────────────┐   git add    ┌────────────────┐   git commit   ┌──────────────────────┐
 │  Working Directory │ ───────────▶ │  Staging Area  │ ─────────────▶ │  Repository (.git)   │
 │                    │              │                │                │                      │
 │ Where you edit     │              │ Where you pick │                │ Where commits are    │
 │ files              │              │ what to commit │                │ permanently stored   │
 └────────────────────┘              └────────────────┘                └──────────────────────┘
```

**Flow: Modify → Add → Commit → Repeat**

### Why does the staging area exist?

Because you don't always want to commit *everything* you changed. Say you fixed a bug **and** reformatted a file. With staging you can make two clean commits:

```bash
git add bugfix.md
git commit -m "Fix typo in installation steps"

git add formatting.md
git commit -m "Reformat tables in formatting.md"
```

### File states

A file in a Git repo is always in one of these states:

- **Untracked** — Git doesn't know about it yet
- **Modified** — changed, but not staged
- **Staged** — marked to go into the next commit
- **Committed** — safely stored in history

`git status` shows you which state every file is in.

---

## 6. The Basic Workflow

```bash
# 1. Start a repo (or clone an existing one)
git init
# or
git clone <url>

# 2. Make changes to files (use your editor)

# 3. Check what changed
git status
git diff

# 4. Stage the changes
git add <file>        # one file
git add .             # everything in this folder

# 5. Commit them
git commit -m "Describe what you did"

# 6. Share them (if you have a remote)
git push
```

---

## 7. Essential Commands

### Setup

| Command | What it does |
|---------|--------------|
| `git config --global user.name "Name"` | Set your name for commits |
| `git config --global user.email "email"` | Set your email for commits |
| `git init` | Turn the current folder into a Git repo |
| `git clone <url>` | Copy a remote repo to your computer |

### Everyday

| Command | What it does |
|---------|--------------|
| `git status` | Show changed, staged, and untracked files |
| `git add <file>` | Stage a specific file |
| `git add .` | Stage all changes in the current folder |
| `git commit -m "message"` | Commit staged changes with a message |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git log` | View commit history |
| `git log --oneline --graph --all` | Compact, visual history of all branches |

### Branches

| Command | What it does |
|---------|--------------|
| `git branch` | List branches |
| `git branch <name>` | Create a branch |
| `git switch <name>` | Switch to a branch (modern) |
| `git switch -c <name>` | Create and switch in one step |
| `git checkout <name>` | Switch to a branch (older, still works) |
| `git merge <branch>` | Merge `<branch>` into your current branch |
| `git branch -d <name>` | Delete a merged branch |

### Remotes

| Command | What it does |
|---------|--------------|
| `git remote -v` | List remotes |
| `git remote add <name> <url>` | Add a remote |
| `git fetch` | Download new commits from remote, **without** changing your files |
| `git pull` | Fetch **and** merge remote changes into your branch |
| `git push` | Upload your commits to the remote |
| `git push -u origin <branch>` | Push a new branch and set it to track the remote |

### Inspecting & Saving Work

| Command | What it does |
|---------|--------------|
| `git show <commit>` | Show what changed in a commit |
| `git blame <file>` | Show who last changed each line |
| `git stash` | Temporarily shelve uncommitted changes |
| `git stash pop` | Bring stashed changes back |

---

## 8. Branching & Merging

A **branch** lets you work on something without affecting `main`.

```
main:     A───B───C───────────F   (merge commit)
                   \         /
feature:            D───────E
```

```bash
git switch -c feature-login   # create & move to a new branch
# ...edit, add, commit...
git switch main               # go back to main
git merge feature-login       # bring the feature into main
git branch -d feature-login   # clean up
```

### Fast-forward vs. merge commit

- **Fast-forward:** If `main` hasn't changed since you branched, Git just moves the `main` pointer forward. No extra commit.
- **Merge commit:** If both branches have new commits, Git creates a special commit with two parents that joins them.

### Merge vs. Rebase (brief)

- `git merge` keeps history exactly as it happened, including the branch shape.
- `git rebase` replays your commits on top of another branch, giving a straight-line history.
- **Golden rule:** never rebase commits you've already pushed and shared with others.

---

## 9. Merge Conflicts

A conflict happens when two branches change **the same lines** of the same file. Git doesn't guess. It asks you.

The file will look like this:

```
<<<<<<< HEAD
This is the text on your current branch.
=======
This is the text on the branch you're merging in.
>>>>>>> feature-branch
```

### How to fix

1. Open the file and decide what the final text should be.
2. Delete the `<<<<<<<`, `=======`, and `>>>>>>>` markers.
3. Save, then:

```bash
git add <file>
git commit
```

To give up and go back to before the merge:

```bash
git merge --abort
```

> Conflicts are **normal**, not a sign you did something wrong.

---

## 10. Undoing Things

| Situation | Command |
|-----------|---------|
| Discard changes to a file (not staged yet) | `git restore <file>` |
| Unstage a file (keep the changes) | `git restore --staged <file>` |
| Fix the last commit message (not pushed yet) | `git commit --amend -m "New message"` |
| Add a forgotten file to the last commit (not pushed) | `git add <file>` then `git commit --amend --no-edit` |
| Undo a commit **safely** (even if pushed) | `git revert <commit>` — creates a new commit that undoes it |
| Move branch back, keep changes as unstaged | `git reset <commit>` |
| Move branch back and **throw away** changes | `git reset --hard <commit>` ⚠️ |
| Find "lost" commits | `git reflog` |

> ⚠️ `reset --hard` deletes uncommitted work permanently. When in doubt, use `revert`.
> 💡 `git reflog` is your safety net: it records where HEAD has been, so you can usually recover "deleted" commits.

---

## 11. .gitignore

A `.gitignore` file tells Git which files to **never** track.

```gitignore
# OS junk
.DS_Store
Thumbs.db

# Editor folders
.vscode/
.idea/

# Secrets
.env

# Dependencies & build output
node_modules/
dist/
__pycache__/
*.log
```

Note: `.gitignore` only affects **untracked** files. If a file is already committed, you must untrack it first:

```bash
git rm --cached <file>
```

---

## 12. Common Misconceptions

### ❌ "Git and GitHub are the same thing."
✅ **Git** is the tool on your computer. **GitHub** is a website that hosts Git repositories. You can use Git with no GitHub at all (or with GitLab, Bitbucket, etc.).

### ❌ "Git saves my work automatically."
✅ Nothing is saved in Git until you **commit**. Saving a file in your editor is not the same as committing.

### ❌ "`git commit` uploads my code."
✅ A commit is **local**. Nothing leaves your computer until you `git push`.

### ❌ "`git add` saves my changes."
✅ `git add` only **stages** them for the next commit. If you edit the file again after `git add`, the new edits aren't staged until you add again.

### ❌ "Git stores differences (diffs) between versions."
✅ Conceptually, Git stores **snapshots** of the whole project at each commit. (Internally it compresses efficiently, but the mental model is snapshots, not patches.)

### ❌ "A branch is a copy of all my files."
✅ A branch is just a lightweight **pointer** to a commit. Creating one is nearly instant and costs almost nothing, so use them freely.

### ❌ "`git pull` and `git fetch` are the same."
✅ `fetch` only downloads new commits. `pull` = `fetch` + `merge`, so it changes your files.

### ❌ "If I delete a file, it's gone from history."
✅ It's still in every earlier commit. This is why you must **never commit passwords or API keys**. Even after deleting, they remain in history.

### ❌ "Merge conflicts mean I broke something."
✅ Conflicts just mean two people edited the same lines. Git is asking a human to decide. It's routine.

### ❌ "I need to be online to use Git."
✅ Almost everything (commit, branch, merge, log, diff) works offline. Only push, pull, fetch, and clone need a network.

### ❌ "Git is only for code."
✅ Git works for any text-based files: notes, docs, config, books, research. (This repo is the proof!) It's less useful for large binary files like videos.

### ❌ "Once I commit a mistake, it's permanent."
✅ You can amend, revert, reset, and recover via `reflog`. Git is very hard to truly lose data in, as long as it was committed at some point.

---

## 13. Common Mistakes & Fixes

| Mistake | Fix |
|---------|-----|
| Committed to `main` instead of a branch | `git switch -c new-branch` (takes your commits along), then `git switch main` and `git reset --hard origin/main` |
| Typo in last commit message | `git commit --amend -m "Correct message"` (only if not pushed) |
| Ran `git init` in the wrong folder (like your home folder!) | Delete the `.git` folder in that location |
| `push` rejected: "Updates were rejected" | Someone pushed first. Run `git pull`, fix any conflicts, then push again |
| "detached HEAD" warning | You checked out a commit, not a branch. Run `git switch main` (or `git switch -c new-branch` to keep work) |
| Committed a secret | Rotate/revoke the secret **immediately**. Removing it from history is secondary |
| Forgot what you were doing | `git status` → `git log --oneline` → `git diff` |

---

## 14. Best Practices

- ✍️ **Write meaningful commit messages.** Use the imperative mood: `"Add login page"`, not `"added stuff"`.
- 🔹 **Commit small and often.** One logical change per commit.
- 🌿 **Use branches** for every feature or fix.
- ⬇️ **Pull before you push** to reduce conflicts.
- 🙈 **Use `.gitignore`** for secrets, dependencies, and build files.
- 👀 **Review before committing** with `git status` and `git diff --staged`.
- 🔐 **Never commit passwords, tokens, or `.env` files.**
- 📖 **Keep your README updated.**

---

## 15. Student Contributions

> Add your own notes below! Keep them under a heading with your topic. Example:
>
> ### git stash explained (by @your-username)
> Your explanation here...

<!-- Add new sections below this line -->