# 📘 Git & GitHub Notes — A Learn-by-Doing Repo

Welcome! This repository is a **shared notebook about Git and GitHub**, and also the place where you'll *practice* using them.

The idea is simple: you learn Git by reading the notes, and you learn GitHub by **forking this repo, creating your own branch, adding a file about yourself, and sending a Pull Request**. By the time your first PR is merged, you've already used almost everything described in these files.

---

## 📂 What's Inside

```
.
├── README.md              ← You are here: what this repo is and how to set it up
├── notes/
│   ├── git.md             ← Everything about Git: concepts, commands, workflow, misconceptions
│   └── github.md          ← Everything about GitHub: repos, forks, PRs, issues, misconceptions
└── students/
    ├── _TEMPLATE.md       ← Template for your introduction (don't edit this one)
    └── <your-name>.md     ← Your own introduction file goes here
```

This repo intentionally contains **only text / Markdown files**. No code, no build steps, nothing to install except Git itself.

---

## 🧭 Who Is This For?

- Students who have never used Git before
- People who've used Git a little but get confused by branches, staging, or merge conflicts
- Anyone who wants a clean, beginner-friendly reference they can keep and extend

---

## 🎯 Your First Task

Every student does the same first task:

1. Create a **branch with your name**
2. Add a **file with your name** inside the `students/` folder, introducing yourself
3. Open a **Pull Request**

The steps below walk you through it.

### 🏷️ Naming rule (important!)

Use the **same name** for your branch and your file: all **lowercase**, words joined with **hyphens**, no spaces or special characters.

| Your name | Branch name | File name |
|-----------|-------------|-----------|
| Priya Sharma | `priya-sharma` | `students/priya-sharma.md` |
| Rahul Verma | `rahul-verma` | `students/rahul-verma.md` |
| Ana Lucía Gómez | `ana-lucia-gomez` | `students/ana-lucia-gomez.md` |

> 💡 If two students have the same name, add something extra, like `rahul-verma-2` or your GitHub username.

---

## 🛠️ Step 1 — Install & Configure Git

### Install

| OS | How |
|----|-----|
| **Windows** | Download from [git-scm.com](https://git-scm.com/downloads) and run the installer (defaults are fine). This also installs **Git Bash**. |
| **macOS** | Run `git --version` in Terminal. If it's missing, macOS will offer to install it. Or use `brew install git`. |
| **Linux** | `sudo apt install git` (Debian/Ubuntu) or `sudo dnf install git` (Fedora) |

Check that it worked:

```bash
git --version
```

### Configure (one-time setup)

Tell Git who you are. This name and email get attached to every commit you make.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

> 💡 Use the **same email** you use on GitHub so your commits are linked to your profile.

Verify:

```bash
git config --list
```

---

## 🌐 Step 2 — Create a GitHub Account

1. Go to [github.com](https://github.com) and sign up.
2. Verify your email.
3. (Recommended) Turn on two-factor authentication in **Settings → Password and authentication**.

---

## 🍴 Step 3 — Fork This Repository

A **fork** is your own personal copy of this repo, under your GitHub account.

1. Click the **Fork** button at the top-right of this page.
2. Keep the default settings and click **Create fork**.
3. You'll now be on `github.com/<your-username>/<this-repo-name>`.

---

## 💻 Step 4 — Clone Your Fork to Your Computer

On **your fork's** page, click the green **Code** button and copy the HTTPS URL. Then:

```bash
git clone https://github.com/<your-username>/<this-repo-name>.git
cd <this-repo-name>
```

Connect your copy to the original repo so you can pull future updates:

```bash
git remote add upstream https://github.com/<original-owner>/<this-repo-name>.git
git remote -v
```

You should see two remotes:
- `origin` → your fork
- `upstream` → the original repo

---

## 🌿 Step 5 — Create a Branch With Your Name

Never work directly on `main`. Create a branch named after **you** (see the naming rule above):

```bash
git switch -c <your-name>
```

Example:

```bash
git switch -c priya-sharma
```

(Older equivalent: `git checkout -b priya-sharma`)

Check you're on the right branch:

```bash
git branch
```

The branch with a `*` next to it is the one you're on.

---

## ✍️ Step 6 — Create Your Introduction File

Copy the template into a new file with your name, inside the `students/` folder:

```bash
cp students/_TEMPLATE.md students/<your-name>.md
```

Example:

```bash
cp students/_TEMPLATE.md students/priya-sharma.md
```

> 🪟 On Windows Command Prompt (not Git Bash), use `copy students\_TEMPLATE.md students\priya-sharma.md` instead. Or just create the file in your editor and paste the template in.

Now open **your** file in any text editor (VS Code, Notepad, etc.) and:

1. Delete the "How to Use This Template" section at the top.
2. Fill in your name, where you're from, your ambition, skills, hobbies, and the rest.
3. Save the file.

> ⚠️ **Only edit your own file.** Don't change `_TEMPLATE.md` or anyone else's file.
>
> 🔐 **Privacy:** This repo may be public. Don't include your phone number, home address, personal email, or date of birth.

---

## ✅ Step 7 — Stage, Commit, Push

```bash
git status                                   # you should see your new file in red
git add students/<your-name>.md              # stage your file
git status                                   # now it should be green
git commit -m "Add introduction for <your-name>"
git push -u origin <your-name>               # upload your branch to YOUR fork
```

Example:

```bash
git add students/priya-sharma.md
git commit -m "Add introduction for priya-sharma"
git push -u origin priya-sharma
```

---

## 🔁 Step 8 — Open a Pull Request

1. Go to your fork on GitHub. You'll see a banner: **"Compare & pull request"**. Click it.
2. Make sure the PR goes **from** `your-username/<your-name>` **into** `original-owner/main`.
3. Title it: `Add introduction for <your-name>`
4. Click **Create pull request**.

A maintainer will review it, maybe leave comments, and merge it. 🎉 That's your first open-source contribution!

> 🛠️ **Need to fix something after opening the PR?** Just edit your file, then `git add`, `git commit`, and `git push` again on the same branch. The PR updates automatically.

---

## 📝 After Your First PR: Add Notes

Once your introduction is merged, you can contribute notes to `notes/git.md` or `notes/github.md`:

- A concept explained in your own words
- A command that confused you and how you figured it out
- A misconception you had
- A mistake you made and how you fixed it

For each new contribution, **sync your fork first** (see below), then create a new branch with a descriptive name:

```bash
git switch main
git pull upstream main
git switch -c <your-name>-git-stash-notes
```

Then add, commit, push, and open a PR the same way as before.

---

## 🔄 Keeping Your Fork Up to Date

Other students' files and notes will get merged over time. To get them into your fork:

```bash
git switch main
git pull upstream main
git push origin main
```

Or click **Sync fork** on your fork's GitHub page, then run `git pull` locally.

---

## 📏 Contribution Guidelines

To keep the repo clean and useful for everyone:

1. **Follow the naming rule.** Branch and file both use your name in lowercase-with-hyphens.
2. **Your introduction goes only in `students/<your-name>.md`.** Never edit someone else's file or the template.
3. **Notes go in the right file.** Git concepts → `notes/git.md`. GitHub features → `notes/github.md`.
4. **Put notes under the right heading.** If no heading fits, create a new one.
5. **Don't delete other people's notes.** Improve or clarify them instead.
6. **Keep it beginner-friendly.** Explain jargon the first time you use it.
7. **Test your commands.** If you add a command, make sure it actually works.
8. **One topic per PR.** Small PRs are easier to review and less likely to conflict.
9. **Write a meaningful commit message.** `"Add explanation of git rebase"` ✅ — `"update"` ❌
10. **Never commit to `main`.** Always use a branch.

---

## 🆘 Stuck?

- Run `git status`. It almost always tells you what's going on and what to do next.
- **Committed on `main` by mistake?** Run `git switch -c <your-name>` to move your work onto a new branch, then push that branch.
- **Push rejected or asking for a password?** GitHub needs a Personal Access Token or SSH key, not your account password. See section 9 of `notes/github.md`.
- Open an **Issue** in this repo describing your problem.
- Check the "Common Mistakes" sections in `notes/git.md` and `notes/github.md`.

---

## 🧠 Remember

> **Code. Commit. Contribute. Repeat.**
>
> The more you use Git & GitHub, the more confident you'll become.

Happy learning! 🚀